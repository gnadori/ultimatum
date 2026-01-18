# Ultimátum Játék (Ultimatum Game)

Ez egy valós idejű, többjátékos kísérleti játék, amelyet közgazdaságtani és pszichológiai kísérletekhez terveztek. A játékot egy adminisztrátor irányítja, a játékosok pedig saját eszközükről csatlakozhatnak.

## Funkciók
- **Adminisztrátori Felület (`admin.html`):** Játékok létrehozása, beállítások testreszabása (körök száma, szerepkörök, chat), és eredmények exportálása CSV-ben.
- **Játékos Felület (`index.html`):** Csatlakozás kóddal, játékmenet (ajánlattétel/elfogadás), chat lehetőség.
- **Valós idejű szinkronizáció:** A Firebase technológiának köszönhetően minden azonnal frissül a képernyőkön.
- **Hibaelhárító mód:** Automatikus "Long Polling" használata a szigorúbb hálózati környezetek (pl. iskolai WiFi) támogatására.

## Telepítés és Futtatás

Mivel a játék tisztán HTML/JS alapú és a Firebase szolgáltatást használja, nincs szükség bonyolult szerver telepítésre.

1. **Futtatás:**
   - Nyisd meg az `admin.html` fájlt a böngészőben a játékok létrehozásához.
   - A játékosoknak küldd el az `index.html` linkjét (vagy a generált megosztási linket).

2. **Firebase Beállítás (Ha sajátot használnál):**
   - A jelenlegi verzió már tartalmaz egy működő konfigurációt.
   - Ha saját Firebase projektet szeretnél használni, cseréld ki a `firebaseConfig` részt mindkét fájlban.

## Használati Útmutató

### Adminisztrátor (Tanár/Kísérletvezető)
1. Nyisd meg az `admin.html` oldalt.
2. Állítsd be a játék paramétereit:
   - **Teljes Összeg:** Az elosztandó pénz mennyisége.
   - **Körök Száma:** Hány körből álljon a játék.
   - **Szerepkörök:** 
     - *Fix:* Mindig ugyanaz az Ajánlattevő.
     - *Váltakozó:* Körönként cserélnek.
     - *Véletlenszerű:* Minden körben véletlenszerű.
   - **Chat:** Engedélyezed-e a kommunikációt.
3. Kattints a **"Játék Létrehozása"** gombra.
4. Oszd meg a **6-jegyű kódot** vagy a **linket** a két játékossal.
5. A játék végén a **"CSV Letöltés"** gombbal kimentheted az adatokat Excel-kompatibilis formátumban.

### Játékosok
1. Nyissák meg az `index.html` oldalt (vagy a kapott linket).
2. Írják be a kapott kódot és kattintsanak a **"Csatlakozás"** gombra.
3. Várjanak, amíg a másik játékos is csatlakozik.
4. **Ajánlattevő:** Beállítja az összeget és elküldi az ajánlatot.
5. **Válaszoló:** Elfogadja vagy elutasítja az ajánlatot.
   - *Elfogadás:* A pénz eloszlik a megegyezés szerint.
   - *Elutasítás:* Senki nem kap semmit.

## Hibaelhárítás
- **"Connection timed out" / Hálózati hiba:** Ellenőrizze az internetkapcsolatot. Az iskolai tűzfalak néha blokkolhatják a kapcsolatot; a játék beépített "Long Polling" módja ezen segít, de extrém esetben mobilnet használata javasolt.
- **Nem töltődnek be a játékok:** Frissítsd az oldalt. Győződj meg róla, hogy a Firebase projekt "Cloud Firestore" szolgáltatása aktív.
