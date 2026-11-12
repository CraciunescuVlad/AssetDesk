# Scenarii de utilizare

[← Înapoi la README](../README.md)


**Actori:** Angajat (`EMPLOYEE`), Responsabil IT (`IT_STAFF`), Manager (`MANAGER`).




## Use case 1: Atribuirea unui echipament și confirmarea primirii

**Actori:** Responsabil IT, Angajat 

**Scop:** angajatul primește un echipament, iar predarea are o dovadă digitală

**Precondiții:**
- responsabilul IT și angajatul au conturi active
- echipamentul are starea „Disponibil” și nu are nicio atribuire activă

**Flux principal:**
1. Responsabilul IT selectează un echipament din inventarul aplicației, alege angajatul din lista de angajați si confirmă
2. Sistemul scrie în istoricul echipamentului: atribuit lui <Angajat> de <Staff Member>
3. Angajatul se autentifică și vede pe dashboard atribuirea pe care trebuie să o confirme
4. Sistemul marchează atribuirea „Confirmată”, salvează data confirmării și trece echipamentul în „În uz”


**Fluxuri alternative:**
- **1a.** Echipamentul are deja o atribuire activă: nu se poate apăsa butonul de atribuire
- **4a.** Angajatul refuză atribuirea

**Postcondiții:** echipamentul este „În uz”, atribuirea este „Confirmată”


---

## Use case 2: Refuzul unei atribuiri

**Actori:** Angajat, Responsabil IT 

**Precondiții:** există o atribuire „În așteptare” pentru angajat.

**Flux principal:**
1. Angajatul deschide atribuirea de pe dashboard și apasă „Refuz”
2. Angajatul menționează motivul refuzului și confirmă
3. Sistemul marchează atribuirea „Refuzată” și salvează motivul

**Postcondiții:** atribuirea este „Refuzată”, iar echipamentul este „Disponibil” pentru o nouă atribuire

---

## Use case 3: Returnarea unui echipament defect

**Actori:** Responsabil IT
**Scop:** echipamentul returnat ajunge în starea potrivită, iar starea fizică rămâne consemnată.

**Precondiții:** echipamentul este „În uz”, cu o atribuire „Confirmată”.

**Flux principal:**
1. Angajatul aduce echipamentul, iar Responsabilul IT setează acest echipament ca fiind "Defect", adăugând observații
2. Sistemul salvează starea acestui echipament, iar acesta nu va mai putea fi atribuit către un alt angajat
3. După reparație, Responsabilul IT marchează echipamentul ca fiind reparat, acesta devenind din nou disponibil


**Postcondiții:** atribuirea este „Returnată”, echipamentul este „În service” (sau „Disponibil” după reparație)

---

## Use case 4: Alerta de garanție și casarea unui echipament

**Actori:** Responsabil IT, Manager 
**Scop:** garanțiile care expiră nu trec neobservate

**Precondiții:** există echipamente cu garanția care expiră în următoarele 30 de zile.

**Flux principal:**
1. Responsabilul IT se autentifică și vede pe dashboard secțiunea „Garanții care expiră în 30 de zile”
2. Alege un echipament și obține informații despre acesta   
3. Reînnoiește garanția, dacă echipamentul poate fi folosit în continuare sau alege să-l caseze dacă este prea vechi
4. Managerul vede alerta pe dashboard-ul lui, iar în istoricul echipamentului vede casarea, cine a făcut-o și de ce

**Fluxuri alternative:**
- **3a.** Echipamentul este „În uz”: butonul „Casează” nu este disponibil

**Postcondiții:** echipamentele casate ies din evidență și nu mai pot fi atribuite. Se reactualizează perioada de garanție pentru cele care s-au creat garanții noi


