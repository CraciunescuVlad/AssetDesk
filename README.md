# IT Asset Management

Aplicație web pentru evidența echipamentelor IT într-o firmă de dimensiuni mici: registru cu seriile dispozitivelor, atribuire cu confirmare digitală din partea angajatului, returnare cu verificarea stării fizice, stări controlate, istoric complet și alerte de garanție.

## Documentație

| Document | Conținut |
|---|---|
| [Cerințe](docs/requirements.md) | cerințele funcționale și nefuncționale, prioritizate |
| [Scenarii de utilizare](docs/use-cases.md) | cazurile de utilizare principale|
| [Wireframe-uri](docs/wireframes-2.md/) | ecranele principale și fluxurile de navigare |
| [Arhitectură](docs/architecture.md) | componentele aplicației și comunicarea dintre ele |
| [Modelul de date](docs/data-model.md) | entitățile și relațiile preliminare|
| [Plan de implementare](docs/implementation-plan.md) | tehnologii, versionare, etape și responsabilități |

## Problema

Într-o firmă cu un număr de angajați redus, evidența echipamentelor IT o ține de obicei o singură persoană, responsabilul IT, care se ocupă în paralel și de suport tehnic, achiziții etc.. Echipamentele circulă între angajați, birou și acasă, iar evidența se ține de cele mai multe ori în Excel. Astfel, nimeni nu poate spune sigur ce echipament există, la cine se află, în ce stare e și ce s-a întâmplat cu el.

Consecințele:
- echipamente pierdute sau nereturnate la plecarea angajaților
- reparații plătite pentru că garanția a expirat neobservată
- dispute, certuri
- trasabilitate inexistentă

Excel-ul nu impune nicio regulă, iar aplicațiile mari de gestiune a activelor IT sunt prea complexe pentru o firmă mică. Aplicația noastră stă la mijloc: *reguli stricte, fără configurare grea.

## Obiective

1. **O serie nu poate exista de două ori** în registru
2. **Un echipament nu ajunge „în uz” până când angajatul nu confirmă primirea** din contul lui
3. **Orice modificare rămâne în istoric**
4. Trasabilitate

## Rolurile utilizatorilor

| Rol | Ce face în aplicație |
|---|---|
| **Responsabil IT** (utilizatorul principal) | gestionează echipamentele și conturile, face atribuiri și returnări |
| **Angajat** | vede echipamentele pe care le are în grijă, confirmă sau refuză primirea unui echipament |
| **Manager** | vede inventarul, istoricul și alertele, fără să facă operațiuni |

## Echipa

| Membru | Rol | Responsabilități principale |
|---|---|---|
| **Flavius-Andrei Neamu** | Backend | baza de date, regulile de business |
| **Vlad Crăciunescu** | Frontend | interfața: paginile, navigarea, UI/UX |
| **Raul-Daniel Macovei** | Fullstack | configurarea proiectului, autentificarea și funcționalitățile opționale |



## Funcționalități principale

- autentificare cu trei roluri: angajat, responsabil IT, manager
- registru de echipamente (căutare și filtre)
- atribuirea unui echipament către un angajat, cu confirmare sau refuz din contul angajatului
- returnarea echipamentului 
- alerte pentru garanțiile care expiră în următoarele 30 de zile;
- dashboard custom in functie de rol


## Tehnologii

| Zonă | Tehnologie |
|---|---|
| Backend | Java + Spring Boot |
| Persistență | Spring Data JPA|
| Frontend | React, Typescript|
| Versionare | Git, GitHub |

