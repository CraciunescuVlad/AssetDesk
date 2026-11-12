# Cerințe

[← Înapoi la README](../README.md)

Am prioritizat cerințele după metoda MoSCoW: ce e **Must** intră în prima versiune, iar **Should** și **Could** vin după, dacă ne rămâne timp.

## Cerințe funcționale

| Cerința | Prioritate |
|---|---|
| Utilizatorii se autentifica cu email și parolă. Există trei roluri: angajat, responsabil IT și manager. Conturile le creează responsabilul IT. | Must |
| Responsabilul IT adaugă și editează echipamente  | Must |
| Responsabilul IT atribuie un echipament unui angajat | Must |
| Echipamentul ajunge „în uz” doar după ce angajatul confirmă că l-a primit| Must |
| Tot ce se întâmplă cu un echipament rămâne în istoricul lui, iar istoricul nu poate fi modificat | Must |
| Echipamentele a căror garanție expiră în următoarele 30 de zile apar ca alerte | Must |
| Angajatul poate raporta o problemă tehnică la un echipament | Should |
| Inventarul se poate exporta în Excel sau CSV | Could |


## Cerințe nefuncționale

| Cerința | Prioritate |
|---|---|
| Parolele nu se salvează în clar, iar permisiunile se verifică pe server, nu doar prin ascunderea butoanelor. | Must |
| Interfața e în română, iar mesajele de eroare spun clar ce s-a întâmplat și ce poate face utilizatorul | Must |
| Utilizarea zilnică este ușoară, sistemul oferă o experiență simplu de înțeles | Must |
| Paginile se încarcă în mai puțin de două secunde. | Should |
