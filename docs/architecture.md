# Arhitectura aplicației

[← Înapoi la README](../README.md)

Aplicația are trei componente care rulează separat:

1. **Frontend**: o aplicație React care rulează în browser
2. **Backend**: un API REST scris în Spring Boot
3. **Baza de date**: MySQL

Frontend-ul și backend-ul comunică prin **HTTP cu JSON**


Am ales această variantă pentru că echipa e împărțită pe frontend și backend, și ne permite să lucrăm independent

```mermaid
flowchart LR
    FE[React<br/>în browser]
    subgraph BE[Spring Boot]
        SEC[Securitate<br/>JWT · roluri]
        CTRL[Controllere]
        SRV[Servicii<br/>reguli · mașina de stări]
        REPO[Repository-uri]
        SEC --> CTRL --> SRV --> REPO
    end
    DB[(MySQL)]

    FE -- "HTTP/JSON + JWT" --> SEC
    REPO --> DB
```

## Backend

Codul este împărțit **pe domenii**. Fiecare domeniu are propriul controller, serviciu, repository și entități.

| Domeniu | Ce conține |
|---|---|
| `auth` | login |
| `users` | utilizatori, roluri, departamente |
| `equipment` | echipamentele |
| `assignments` | atribuire, confirmare, refuz, anulare, returnare |
| `audit` | istoricul operațiunilor |
| `alerts` | alertele de garanție |


## Exemplu de flux: confirmarea unei atribuiri

Vezi și [UC-1](use-cases.md#uc-1-atribuirea-unui-echipament-și-confirmarea-primirii).

```mermaid
sequenceDiagram
    actor A as Angajat
    participant FE as React
    participant BE as Spring Boot
    participant DB as MySQL

    A->>FE: apasă „Confirm primirea”
    FE->>BE: POST /api/assignments/{id}/confirm (cu JWT)
    BE->>DB: citește atribuirea
    alt atribuirea e a altui angajat
        BE-->>FE: 403
    else atribuirea nu mai e „În așteptare”
        BE-->>FE: 409
    else totul e în regulă
        BE->>DB: atribuirea devine confirmată, echipamentul trece „În uz”, se scrie în istoric
        BE-->>FE: 200 OK
        FE-->>A: „Ai confirmat primirea echipamentului.”
    end
```

## Securitate

- Parolele nu sunt salvate niciodată în text clar
- Fiecare endpoint are declarat rolul permis. În plus, un angajat poate confirma sau refuza doar atribuirile lui

## Tratarea erorilor

Orice eroare ajunge la frontend în același format:

```json
{
  "status": ...,
  "error": "Conflict",
  "message": "example"
}
```

Frontend-ul afișează direct câmpul `message`, care e scris în română.

## Rulare locală

```mermaid
flowchart LR
    subgraph PC[Calculatorul dezvoltatorului]
        V[Browser]
        SB[Spring Boot]
        subgraph Docker
            M[MySQL]
        end
    end
    V -- HTTP --> SB --> M
```