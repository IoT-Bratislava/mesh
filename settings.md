# Odporúčané nastavenia

- Preset: **EU/UK (Narrow)**
- Frekvencia (MHz): **869.618 MHz**
- Šírka pásma: **62.5 kHz**
- Spreading Factor(SF):  **8**
- Coding Rate(CR): **5 (pozor - zmena oporti presetu)**

## Klienti
K nastaveniam sa dostanete cez ozubené koliesko v hlavnom menu
- Nastavenia kontaktov
  - Vyberte 'Automaticky pridať vybrané'
  - Nechajte len 'Automaticky pridávať používatelov', ostatné Automatické pridávania vypnite
  - Zapnite 'Prepísať najstarší'
- Nastavenie správ
  - Nastavte 'Potvrdenia priamych správ' na 2
- Experimentálne nastavenia
  - Nastavte 'Veľkosť hashu trasy' na '2 bajtový'
Nezabudnite si nastavit aj [regionálne kanály](./channels.md)

## Repeatre
Vačšinu nastavení si môžete zmeniť hneď po naflashovaní repeatra cez USB na https://config.meshcore.io
1. Je vhodné nastaviť `Flood Advert Interval` na 47h, aby sme znížili zaťaženie siete veľkými redundantnými packetmi. Rovnako je dobré nechať zero-hop advert interval na 0, kedže reálne využitie má len pri susedoch a tí sa dajú vyžiadať manuálne, keď to potrebujeme.
2. Nastavením `Coding Rate` na `5` znížime airtime skoro na polovicu.
3. Vyplnením `Owner Info` dáme možnosť ostatným kontaktovať majiteľa repeatra a tak možnosť spoločne koordinovať zmeny v sieti.
   Príklad:
   ```
   Owner: recrof <recrof@gmail.com>

   Part of EmpireMesh
   https://mesh.om3kff.sk/
   ```
5. Odporúčané je tiež vypnúť `guest` heslo, aby užívateľ mal prístup ku štatistikám, `Neighbours` a `Owner Info`

### Meno repeatra

V Slovenskom meshi máme jednoduché názvoslovie pre všetky repeatre:
`SK-{Okres}-{Nazov-Lokality}` kde `{Okres}` je dvojpísmenný kód okresu a `{Nazov-Lokality}` môže byť čokoľvek od obce, názvu kopca, alebo iný jasný identifikátor lokality. Prosím nepoužívajte diakritiku, vždy začnite po pomlčke veľkým písmenom a nepoužívajte v názve medzery.
Pre referenciu môžete pozrieť aj [zoznam skratiek okresov](https://lstn.juls.savba.sk/minfo/skratky-okresy).

Príklad: `SK-SC-Nova-Dedinka` alebo `SK-BS-Sitno`

Všetkým repeatrom prosím uvedte približnú polohu, aby sa dali jednoducho používať nástroje ako Neighbours alebo Map trace.

**Prosím nepoužívajte toto názvoslovie pri klientoch - mätie to užívateľov**

### Regióny

Regióny slúžia na izoláciu flood prevádzky do väčších alebo menších segmentov.
Dnes ich môžeme použiť napríklad na regionálne kanály, ktoré, ak sú nastavené správne, vedia držať flood prevádzku len v jednej lokalite.
Pre hlavný slovenský región sme vybrali značku `sk`, ostatné regióny majú formát `sk-{okres}`. Pre referenciu môžete pozrieť aj [zoznam skratiek okresov](https://lstn.juls.savba.sk/minfo/skratky-okresy). Značky sú zadávané vždy malými písmenami.

Tu je príklad nastavenia regiónov na jednom z repeatrov:

<img src="img/App_Scopes.png" alt="Nastavenie regiónov" style="max-width: 100%; height: 250px"/>

Pozor: Je dôležité, aby bol povolený aj Global(`*`) región, v opačnom prípade prestane repeater preposielať ne-regionálnu flood prevádzku ako adverty, flood management a flood privátne správy. Od verzie 1.15.0 sa ale dá nastavit vychodzí región, ktory vie pracovať aj so zakázaným globalom(`*`).
Kanálu `#slovakia` sa odporúča nastavenie regiónu `sk`, keďže vačšina repeatrov má už regióny nakonfigurované, tak isto má zmysel nastavit lokálny okresný región kanálom ako `#martin` (sk-mt), `#kosice` (sk-ke), `#bratislava` (sk-ba), atď..

### Kolízie ID

Pri prvom štarte repeatra sa často stane, že sa vygeneruje ID(prvý bajt) verejného kľúča, ktorý sa už v sieti používa. Routing bude ďalej fungovať, avšak sťaží to presnú identifikáciu cesty, preto sa odporúča upraviť kľúč, aby používal voľné ID.
Tu je jednoduchý návod ako odstrániť ID kolíziu. Na zmenu ID na repeatri je potrebný aspoň firmware vo verzii 1.12.0:

1. Na [EmpireMesh stránke pre ID kolízie](https://map.meshcore.hu/#/analytics) (zalozka Hash Issues) je vidno všetky voľné ID čiernou farbou - jedno si vyberte.
2. Po prihlásení na repeater cez MeshCore App choďte do `Settings` > `Change Identity Key`.
3. Kliknite na `Choose prefix` a zadajte voľné ID z prvého kroku a dajte `OK`.
4. Odzálohujte si nový verejný a súkromný kľúč, keby ho v budúcnosti trebalo obnoviť.
5. Potvrďte novo vygenerovaný kľúč vpravo hore cez tlačidlo `✔`.
6. Repeater sa reštartuje a pošle advert s novým kľúčom - kontakt so starým kľúčom je možné zmazať.

## Aktualizácie firmware cez Bluetooth/Wifi

### OTA pre nRF52 (Bluetooth)
Medzi tieto zariadenia patrí napríklad: RAK 4631, Seeed Studio Xiao nRF52840, Sensecap Solar P1, Heltec t114...

Predtým ako sa pokúsite o vzdialenú aktualizáciu, veľmi odporúčame zmeniť bootloader na [OTAFIX(verzia 2.1 a vyššie)](https://github.com/oltaco/Adafruit_nRF52_Bootloader_OTAFIX/releases).
Na upgrade bootloadera je potrebné byť pripojený na repeater cez USB kábel.

Stačí stiahnuť UF2 súbor pre zariadenie, ktoré chcete aktualizovať, dvoj-kliknúť tlačidlo RESET, ktoré by malo otvoriť USB disk, do ktorého treba nahrať stiahnutý UF2 súbor.
Po dokončení kopírovania a zmiznutí USB disku je bootloader aktualizovaný a môžete si overiť, či sa správne aktualizoval pomocou opätovného dvoj-kliku a následného prečítania súboru `INFO_UF2.TXT`, v ktorom by sa mal nachádzať reťazec OTAFIX s verziou.

1. Stiahnite si aplikáciu nRF DFU: [Android Play Store](https://play.google.com/store/apps/details?id=no.nordicsemi.android.dfu), alebo [Apple App Store](https://apps.apple.com/us/app/nrf-device-firmware-update/id1624454660).
2. Na [stránke flashera](https://flasher.meshcore.dev) vyberte zariadenie, ktoré chcete aktualizovať, vyberte `Repeater`, stlačte tlačidlo Download a vyberte súbor s príponou `.zip`
3. V aplikácii MeshCore sa prihláste do repeatera, ktorý chcete aktualizovať
4. Prejdite na záložku `Command Line`, napíšte: `start ota` a potvrdte
5. Mali by ste vidieť odpoveď OK, ktorá potvrdzuje, že zariadenie je teraz v OTA režime. Ak neprišla žiadna odpoveď, pošlite príkaz `start ota` znova
6. Spustite aplikáciu DFU, kliknite na ikonu nastavení v pravom hornom rohu
7. Povoľte `Packets receipt notifications` a zmeňte `Number of Packets` na `8`
8. Povoľte `Force Scanning`
9. Zatvorte nastavenia
10. V rámci `File` vyberte `Choose` a nájdite súbor .zip, ktorý ste stiahli z Flashera
11. Vyberte zariadenie, ktoré chcete aktualizovať – malo by sa volať `XXXXX_OTA` kde `XXXXX` je skrátený názov zariadenia
12. Kliknite na `Upload` a začne sa aktualizácia
13. Ak aktualizácia zlyhá, skúste vypnúť a znova zapnúť Bluetooth na svojom telefóne a začnite odznova, ak to nepomôže, skúste reštartovať telefón.
14. Počkajte na dokončenie aktualizácie. Môže to trvať niekoľko minút
15. Po aktualizácii by sa malo zariadenie automaticky reštartovať

### OTA pre ESP32 (WiFi)
Medzi tieto zariadenia patrí napríklad: Heltec v3, v4, WSL3, Seeed Studio Xiao ESP32(s3/c3/c6..),

1.  Na [stránke flashera](https://flasher.meshcore.dev) vyberte zariadenie, ktoré chcete aktualizovať, vyberte `Repeater`, stlačte tlačidlo Download a vyberte súbor s príponou `.bin`, ktorý nemá v názve `merged`
2. V aplikácii MeshCore sa prihláste do repeatera, ktorý chcete aktualizovať
3. Prejdite na záložku `Command Line`, napíšte: `start ota` a potvrďte
4. Mali by ste vidieť odpoveď OK, ktorá potvrdzuje, že zariadenie je teraz v OTA režime. Ak neprišla žiadna odpoveď, pošlite príkaz `start ota` znova
5. Skopírujte si odpoveď repeatra - obsahuje webovú adresu
6. Pripojte sa na novo vytvorenú WiFi sieť s názvom `MeshCore-OTA`.
7. Otvorte prehliadač a zadajte webovú adresu z kroku č.4
8. V rámci formulára kliknite na výber súboru a nájdite stiahnutý súbor z kroku č.1 a potvrďte.
9. Po aktualizácii by sa malo zariadenie automaticky reštartovať

## Plánovanie – Pokrytie – Pomôcky

Okrem premerania zarušenia spektra nám pri plánovaní vhodného umiestnenia repeatera pomáhajú aj nástroje priamo v aplikácii (v podmenu **Tools**).
Sú to:

- **Line of Sight** – výškogram medzi dvoma bodmi na mape – vidíte, či vám nezavadzia hora alebo iná prekážka.
- **Map Coverage** – pokrytie priamou vlnou oblasti, kde si prajete mať repeater.
- **Neighbors** (v menu repeatera) – ak už máte repeater, funkcia vám ukáže susedné repeatre, ktoré váš repeater počuje, vrátane sily signálu(SNR). Noví susedia sa pridajú vtedy, keď váš repeater začuje od suseda priamy advert.

<table style="width:100%; border-collapse:collapse; text-align:center;">
  <tr>
    <td style="width:32%; padding:5px;">
      <img src="img/App_LineOfSight.jpg" alt="App: Line of Sight" style="width:100%; height:350px; object-fit:cover;"/>
    </td>
    <td style="width:32%; padding:5px;">
      <img src="img/App_AntCoverage.jpg" alt="App: Antenna Coverage" style="width:100%; height:350px; object-fit:cover;"/>
    </td>
    <td style="width:32%; padding:5px;">
      <img src="img/App_Neighbours.jpg" alt="App: Neighbours" style="width:100%; height:350px; object-fit:cover;"/>
    </td>
  </tr>
  <tr>
    <td>App: Line of Sight</td>
    <td>App: Antenna Coverage</td>
    <td>App: Neighbours</td>
  </tr>
</table>
