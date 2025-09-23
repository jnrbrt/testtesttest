# Rendszerterv – Egyszerű Hírportál

## 1. A rendszer célja

A rendszer célja egy egyszerű webes hírportál létrehozása, amely lehetővé teszi a felhasználók számára a legfrissebb hírek gyors és átlátható elérését. A portál célja, hogy a hírek könnyen kategorizálhatók és kereshetők legyenek, így a látogatók kényelmesen böngészhetnek különböző témákban.

A portál nem foglal magában komplex interaktív funkciókat, mint például felhasználói fiókok létrehozása vagy hozzászólások írása. Ezzel tisztázzuk a projekt hatókörét: a cél a tartalom megjelenítése és egyszerű kezelhetősége.

**Alcélok:**

- Gyors betöltési idő biztosítása minden eszközön.
- Mobilbarát megjelenés a felhasználói élmény növelése érdekében.
- Egyszerű és könnyen karbantartható kódstruktúra kialakítása.

## 2. Projekt terv

### 2.1 Projekt szerepkörök és felelősségek

- **Megrendelő**: meghatározza az elvárásokat, jóváhagyja a projekt mérföldköveit, ellenőrzi az átadott verziókat.  
- **Projektvezető**: felel a projekt ütemezéséért, koordinálja a csapatot, dokumentálja a folyamatokat és a döntéseket.  
- **Frontend fejlesztő**: HTML, CSS és JavaScript fejlesztés, a felhasználói felület megvalósítása.  
- **Tesztelő**: a funkciók működésének ellenőrzése, hibák rögzítése, javaslat a fejlesztői javításokra.  

### 2.2 Fejlesztő eszközök

- VS Code, mint fő fejlesztői környezet.  
- Git verziókezelés a kód nyomon követéséhez.  
- Böngésző fejlesztői eszközök (Chrome/Firefox), hibakereséshez és teljesítmény elemzéshez.  

### 2.3 Ütemterv és mérföldkövek

- **Kezdő fázis**: követelmények rögzítése, tervezési alapok meghatározása.  
- **Fejlesztési fázis**: HTML alapok, CSS stílus és elrendezés, JavaScript funkciók.  
- **Tesztelési fázis**: integrációs és funkcionális tesztek, hibajavítások.  
- **Átadás**: MVP verzió bemutatása, visszajelzések gyűjtése, végső finomhangolás.  

## 3. Üzleti folyamatok modellje

### 3.1 Üzleti szereplők

- **Felhasználó**: látogatja az oldalt, böngészi a híreket, szűr, keres és olvas.  
- **Rendszer**: felelős a hírek megjelenítéséért, kategorizálásáért, keresés és lapozás biztosításáért.  

### 3.2 Üzleti folyamatok

A felhasználó a főoldalon elindulva a híreket kategória vagy kulcsszó alapján szűrheti. A részletes cikk megtekintése után visszatérhet a listaoldalra, vagy lapozhat a következő hírekhez.

**Folyamat lépései:**

1. Főoldal megnyitása.  
2. Hírek listázása, alapértelmezett időrend szerint.  
3. Kategória szerinti szűrés alkalmazása.  
4. Kulcsszó alapján történő keresés.  
5. Részletes cikk megtekintése.  
6. Lapozás a következő oldalakra, ha nagyobb számú hír van.  

### 3.3 Üzleti entitások

- **Hír**: tartalmazza a címet, kivonatot, teljes szöveget, dátumot és kategóriát.  
- **Kategória**: azonosító és név alapján csoportosítja a híreket.  

#### Ábra: Üzleti folyamat diagram
```mermaid
flowchart TD
  A[Főoldal] --> B[Hírek listázása]
  B --> C[Kategória szűrés]
  B --> D[Keresés kulcsszó alapján]
  C --> E[Részletes nézet]
  D --> E
  E --> F[Lapozás következő oldalakra]
```

## 4. Követelmények

### 4.1 Funkcionális követelmények

- Hírek listázása időrendben a főoldalon.  
- Kategóriák szerinti szűrés lehetősége.  
- Kulcsszavas keresés címben és szövegben.  
- Részletes cikk megtekintése, teljes szöveggel és metaadatokkal.  
- Lapozás nagy elemszám esetén.  
- Hibakezelés: „Nincs találat” és 404 oldal megjelenítése.

### 4.2 Nem funkcionális követelmények

- Egyszerű, letisztult felhasználói felület, könnyen áttekinthető navigációval.  
- Gyors betöltési idő és stabil működés minden modern böngészőben.  
- Könnyen karbantartható, moduláris kódstruktúra.  
- Alapvető böngésző kompatibilitás biztosítása, különböző képernyőméreteken is.

## 5. Funkcionális terv

### 5.1 Rendszer szereplők

- **Felhasználó:** böngészi a híreket, keres és szűr.  
- **Rendszer:** biztosítja a hírek elérhetőségét, keresés és szűrés funkciókat.

### 5.2 Használati esetek

```mermaid
usecaseDiagram
actor Felhasználó
Felhasználó --> (Hírek listázása)
Felhasználó --> (Keresés kulcsszó alapján)
Felhasználó --> (Kategória választás)
Felhasználó --> (Részletes nézet megnyitása)
Felhasználó --> (Lapozás több oldal esetén)
```

## 5.3 Határ osztályok

- **index.html**: főoldali hírek listája, kategória szűrő és keresőmező.  
- **article.html**: részletes cikk megtekintés, metaadatokkal együtt.

## 5.4 Menü hierarchia

```mermaid
flowchart TD
  Home[Főoldal] --> News[Hírek listája]
  Home --> Filter[Kategóriák szerinti szűrés]
  Home --> Search[Keresőmező]
  News --> Detail[Cikk részletei]
```

# 5.5 Képernyőtervek

- **Főoldal:** hírek listája, kategória szűrő, keresőmező, lapozás.  
- **Részletes nézet:** cím, teljes szöveg, dátum, kategória, vissza gomb.  

```mermaid
graph LR
  Főoldal --> HírekLista
  Főoldal --> Szűrő
  Főoldal --> Kereső
  HírekLista --> RészletesNézet
```

## 6. Fizikai környezet

## 6.1 Fizikai alrendszerek

A rendszer fizikai környezete három fő rétegre épül, amelyek egymással összhangban működnek, de külön-külön is fejleszthetők és karbantarthatók.

### HTML réteg
- Feladata a tartalom strukturált megjelenítése.
- Főoldali hírek listája, részletes cikkek, kategóriák és keresőmező biztosítása.
- Fontos a szabványos és valid HTML használata, hogy minden böngészőben egységesen jelenjen meg a felület.

### CSS réteg
- Kezeli a vizuális megjelenést: színek, betűtípusok, gombok, elrendezés.
- Támogatja a moduláris stílusokat, amelyek könnyen bővíthetők.
- Reszponzív design: mobil, tablet és asztali eszközök támogatása.
- Általános stílusok: gombok, linkek, fejléc és lábléc egységes megjelenése.

### JavaScript réteg
- Felelős a keresés, szűrés és lapozás logikájáért.
- Moduláris felépítés: minden funkció önálló modulban, könnyen karbantartható.
- Kommunikál a HTML réteggel a DOM manipuláció révén és a CSS-sel a dinamikus megjelenítéshez.

```mermaid
flowchart TD
  HTML[HTML réteg] --> CSS[CSS réteg]
  CSS --> JS[JavaScript réteg]
```

## 7. Absztrakt domain modell

## 7.1 Domain specifikáció

A rendszer domain modellje az alábbi fő entitásokra épül, amelyek meghatározzák a hírek kezelésének és megjelenítésének logikáját.

- **Hírek**
  - Minden hír tartalmaz:
    - **Cím**: a hír rövid, informatív címe.
    - **Kivonat**: rövid összefoglaló a cikk tartalmáról.
    - **Teljes szöveg**: a cikk teljes tartalma HTML formátumban.
    - **Dátum**: a hír publikálásának időpontja.
    - **Kategória**: a hírhez tartozó kategória, amely csoportosítja a tartalmat.

- **Kategóriák**
  - Azonosítóval és névvel ellátott csoportok.
  - Segítik a hírek rendezését, szűrését és gyors elérését.

- **Metaadatok**
  - Szerző: a hír írója.
  - Forrás: az eredeti hírforrás.
  - Hivatkozások: kapcsolódó cikkek vagy külső linkek.

```mermaid
classDiagram
  class Hir {
    +cim
    +kivonat
    +tartalom
    +datum
    +kategoria
  }
  class Kategoria {
    +id
    +nev
  }
  Hir --> Kategoria
```

## 8. Architekturális terv

## 8.1 Tervezési minta

A rendszer rétegzett architektúrát követ, amely lehetővé teszi az egyes komponensek elkülönített fejlesztését, tesztelését és karbantartását.

### Rétegek

- **UI réteg (HTML + CSS)**
  - Felhasználói felület megjelenítése.
  - Struktúrált tartalom: főoldali lista, részletes cikkek, kategória szűrő, keresőmező.
  - Reszponzív megjelenés biztosítása mobil, tablet és asztali eszközökön.

- **Logikai réteg (JavaScript)**
  - Felhasználói interakciók kezelése: szűrés, keresés, lapozás.
  - Moduláris felépítés: Hírkezelő, Szűrő, Kereső és Megjelenítő modulok.

- **Adat réteg (JS objektumok / későbbi SQL adatbázis)**
  - MVP-ben: hírek és kategóriák JavaScript objektumokban.
  - Bővített verzióban: normalizált SQL adatbázis a nagyobb adatmennyiség hatékony kezelése érdekében.

```mermaid
flowchart TD
  UI[HTML + CSS] --> Logic[JS logika]
  Logic --> Data[JS objektumok / későbbi SQL]
```

## 8.2 Biztonsági funkciók

A rendszer tervezésénél különös figyelmet fordítottunk az alapvető biztonsági intézkedésekre, mivel a cél egy olvasható és egyszerű hírportál.

- **Csak olvasható tartalom**
  - A felhasználók nem tudnak adatot módosítani, így nincs lehetőség véletlen vagy szándékos adatvesztésre.
  - Az oldalon nem találhatók szerkesztői felületek vagy adminisztrációs modulok.

- **Nincs felhasználói adatbevitel**
  - Nincsenek űrlapok, regisztráció vagy bejelentkezési lehetőségek, így minimalizált a potenciális támadási felület.

- **Minimalizált támadási felület**
  - A rendszer kliensoldali adatkezelést alkalmaz, nincs szerveroldali feldolgozás.
  - XSS, SQL injection és egyéb tipikus webes támadások lehetősége minimális.

---

## 9. Adatbázis terv

A hírek és kategóriák adatainak tárolása és kezelése normalizált módon történik. Az adatbázis terv segíti a későbbi bővítést és a hatékony lekérdezéseket.

### 9.1 Adatszerkezet

- **HIR**
  - `id`: egyedi azonosító (integer)
  - `cim`: a hír címe (string)
  - `kivonat`: rövid összefoglaló (string)
  - `tartalom`: teljes szöveg (string)
  - `datum`: publikáció dátuma (date)
  - `kategoria_id`: a hír kategóriájára mutató azonosító (integer)

- **KATEGORIA**
  - `id`: egyedi azonosító (integer)
  - `nev`: kategória neve (string)

### 9.2 Kapcsolatok

- Minden **Hír** egy **Kategóriához** tartozik (many-to-one kapcsolat).
- A kategóriák segítik a hírek rendszerezését és szűrését.

```mermaid
erDiagram
  HIR {
    int id
    string cim
    string kivonat
    string tartalom
    date datum
    int kategoria_id
  }
  KATEGORIA {
    int id
    string nev
  }
  HIR }o--|| KATEGORIA : tartozik
```

## 10. Implementációs terv

A rendszer implementációja moduláris felépítést követ, amely lehetővé teszi a könnyű karbantartást és a jövőbeni bővítést. A frontend, a logikai és az adatkezelő modulok különálló fájlokban kerülnek megvalósításra.

### 10.1 Moduláris felépítés

- **HTML fájlok:** a tartalom struktúrájának megjelenítéséért felelősek.  
  - `index.html`: főoldali hírek listája, kategória szűrő, keresőmező.  
  - `article.html`: részletes cikk nézet, metaadatokkal együtt.

- **CSS fájlok:** a vizuális megjelenésért felelősek, reszponzív és moduláris stílusokkal.  
  - Gombok, linkek, fejléc, lábléc, alapvető elrendezések.

- **JavaScript modulok:** a keresés, szűrés, lapozás logikáját kezelik.  
  - `Hirkezelo.js`: hírek betöltése, tárolása, rendezése.  
  - `Szuro.js`: kategóriák és időrend szerinti szűrés.  
  - `Kereso.js`: kulcsszavas keresés a címekben és szövegekben.  
  - `Megjelenito.js`: HTML és CSS koordinálása, reszponzív megjelenítés biztosítása.

### 10.2 Frontend funkciók

- **Hírlap lista:** címmel, kivonattal, dátummal és kategóriával.  
- **Keresés:** kulcsszavas keresés a címek és szövegek között.  
- **Szűrés:** kategóriák alapján történő hírlistázás.  
- **Részletes cikk nézet:** teljes szöveg és metaadatok.  
- **Lapozás:** nagyobb hírmennyiség kezelése több oldalon keresztül.

### 10.3 Kódolási alapelvek

- **Olvashatóság:** jól kommentált, tiszta kód.  
- **Modularitás:** minden modul önálló felelősségi körrel rendelkezik.  
- **Újrafelhasználhatóság:** komponensek könnyen átvihetők más projektekbe.  
- **Bővíthetőség:** további funkciók (pl. kommentek, felhasználói fiókok) könnyen integrálhatók.

```mermaid
flowchart LR
  HTML[HTML] --> CSS[CSS]
  HTML --> JS[JS modulok]
  JS --> HírekLista
  JS --> Kereső
  JS --> Szűrő
```

## 11. Telepítési terv

A telepítési terv célja, hogy a fejlesztett hírportál stabilan és megbízhatóan kerüljön fel a web szerverre, biztosítva a folyamatos működést a felhasználók számára.

### 11.1 Telepítési lépések

1. **Fájlok feltöltése:**  
   - HTML, CSS és JS fájlok FTP/SFTP segítségével kerülnek a web szerverre.  
   - A képek, ikonok és egyéb statikus tartalmak külön könyvtárban kerülnek tárolásra.

2. **Verziókezelés:**  
   - Git használata a kód változásainak nyomon követéséhez.  
   - Commitok és branch-ek biztosítják a verziók visszaállíthatóságát és a csapatmunkát.

3. **Kézi deploy és ellenőrzés:**  
   - Böngészőben történő tesztelés különböző eszközökön (mobil, tablet, desktop).  
   - Hibák, reszponzivitási problémák, betöltési idők ellenőrzése.

```mermaid
flowchart TD
  Dev[Fejlesztői gép] --> Git[Git verziókezelés]
  Git --> Server[Web szerver]
  Server --> Browser[Felhasználó böngésző]
```

## 12. Karbantartási terv

A karbantartási terv célja, hogy a hírportál hosszú távon stabilan és megbízhatóan működjön, valamint gyorsan reagáljon a felhasználói igényekre és hibákra.

### 12.1 Hibajavítás

- **Folyamat:** minden felfedezett hiba manuális teszteléssel kerül azonosításra és javításra a fejlesztők által.  
- **Kategorizálás:** hibák fontosság szerint kerülnek rangsorolásra:
  - Kritikus: azonnali beavatkozást igényel, a rendszer működését akadályozza.
  - Közepes: funkciók részleges kiesése, felhasználói élményt rontja, de a portál működőképes.
  - Alacsony prioritás: kisebb hibák, amelyek nem befolyásolják alapvetően a működést.
- **Dokumentáció:** minden hiba rögzítése Git issue trackerben, a javítások nyomon követhetők és visszakövethetők.

### 12.2 Funkcióbővítés

- **Új funkciók:** a felhasználói visszajelzések és igények alapján kerülnek hozzáadásra.  
- **Példák:**
  - Új kategóriák és címkék létrehozása a hírek jobb szűréséhez.
  - Keresési funkciók kiterjesztése, például dátum vagy szerző alapján.
  - Hosszabb távon felhasználói fiókok és hozzászólások integrálása.

### 12.3 Verziókövetés és adatbiztonság

- **Verziókövetés:** minden kód- és adatbázis-módosítás Git-ben történik, így könnyen visszaállíthatók korábbi állapotok.
- **Dokumentálás:** verziók leírása, változások nyilvántartása, fejlesztési jegyzetek rögzítése.
- **Mentések:** rendszeres adat- és kódmentések biztosítják az adatvesztés elleni védelmet, gyors helyreállítási lehetőséget biztosítva.

```mermaid
flowchart TD
  Kód[Kód és adat] --> GitRepo[Git verziókezelés]
  GitRepo --> Mentés[Rendszeres mentések]
  Mentés --> Helyreállítás[Korábbi verzió visszaállítása]
```

### 12.4 Karbantartási ciklus

A karbantartási ciklus célja a hírportál folyamatos megbízhatóságának és felhasználói élményének biztosítása. A ciklus rendszeres ellenőrzéseket és dokumentált folyamatokat tartalmaz.

- **Rendszeres ellenőrzés:** 
  - A rendszer funkcióinak és teljesítményének heti/heti rendszerességgel történő ellenőrzése.
  - Automatikus és manuális tesztelések kombinációja a hibák korai észlelésére.
  
- **Hiba- és funkciójelentések:** 
  - Minden új hiba és felhasználói igény rögzítése dokumentált formában a verziókezelő rendszerben.
  - Prioritások megadása, hogy a kritikus hibák és fontos funkciók elsőbbséget kapjanak.

- **Frissítések tervezése:** 
  - Az új funkciók és hibajavítások ütemezése a következő fejlesztési ciklusokra.
  - Minden frissítés előzetes tesztelésen és jóváhagyáson megy keresztül a minőség biztosítása érdekében.

```mermaid
flowchart TD
  Tesztelés[Heti/Havi tesztelés] --> HibákRögzítése[Hibák és funkcióigények dokumentálása]
  HibákRögzítése --> Prioritás[Prioritások meghatározása]
  Prioritás --> Fejlesztés[Frissítések és hibajavítások ütemezése]
  Fejlesztés --> Tesztelés
```