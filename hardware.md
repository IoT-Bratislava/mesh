## 🔧 Odporúčané zariadenia

Pre technológiu **MeshCore** (aj Meshtastic) sú vhodné rovnaké typy zariadení. Výber závisí od plánovaného použitia:

### Vhodné ako klient (Companion Radio Ble)
- **[Seeed Studio Wio L1 Tracker](https://www.seeedstudio.com/Wio-Tracker-L1-Pro-p-6454.html)**
  - Kompaktné rozmery
  - Výdrž batérie niekoľko dní
  - Vstavané GPS

- **[LilyGo T-Deck Plus](https://lilygo.cc/products/t-deck-plus-1)**  
  - All-in-one zariadenie s klávesnicou, batériou a displejom
  - Grafické dotykové rozhranie
  - GPS a offline mapy (na microSD kartu)

### Vhodné ako klient alebo Repeater

**💡 Ak staviate repeater viac info nájdete aj tu:** [👉 Stavba Repeater HW/Info](./howto_repeater_build.md)   

- **[Seeed Studio Xiao nRF52840 + Wio SX1262](https://www.aliexpress.com/item/1005008760784706.html)**
  - Využitie na Repeater primárne (nízka spotreba), ale aj klient
  - Malé rozmery (s batériou a anténou sa zmestí do krabičky od TicTac)
  - Veľmi nízka cena, nízka spotreba
  - Použiteľné cez Bluetooth k mobilu aj ako solárny repeater

- **[RAK Wireless RAK4631 + WisBlock](https://www.aliexpress.com/item/1005006901039995.html)**
  - Využitie na Repeater primárne (nízka spotreba), ale aj klient
  - Modulárne riešenie s vyššou kvalitou spracovania
  - Vyššia cena, ale aj vyššia spoľahlivosť a výdrž 
  - Priama podpora pre solárne panely

- **[Heltec Wireless Stick / V3 / Lora32](https://www.aliexpress.com/item/1005005443005152.html)**
  - Malé rozmery, bez GPS
  - Ideálne pre repeatery alebo statické inštalácie
  - Podpora WiFi

### Vhodné na repeater
- **[Seeed Studio SenseCap Solar Node P1 Pro](https://www.seeedstudio.com/SenseCAP-Solar-Node-P1-Pro-for-Meshtastic-LoRa-p-6412.html)**
  - Plne vodotesný obal, vhodný do exteriéru
  - Vstavaný 5W solárny panel
  - Slot na 4 Li-Ion články (volitelná verzia vrátane 18650 článkov + GPS)
  - sada na pripevnenie ku stĺpu alebo konzole

---

📦 Zariadenia sa kupujú cez známe portály ako **Aliexpress, Amazon, RAK Wireless shop** alebo špecializované rádioamatérske obchody.  
⚠️ Dôležité je skontrolovať **čip (napr. SX1262)** a **pásmo (868 MHz)**.

---

## 📡 Antény

Pre spoľahlivý chod siete je dôležitá kvalitná anténa, prispôsobená na pásmo 868 MHz:

### Vhodné na klienta
- [Gizont 17cm laskakit](https://www.laskakit.cz/antena-flexibilni-10dbi-16-7cm-868mhz/)
- [Gizont 17cm aliexpress](https://www.aliexpress.com/item/1005004607615001.html)

### Vhodné na repeater
- [VINNANT Slovakia Y11E-868](https://vinnant.sk/store/page/1?productlist-search=&productlist-sort=created-desc&productlist-categories=868mhz-8695mhz-lorawanheliumflarmsigfox&productlist-tags=&productlist)
- [Antenna LoRa Fiberglass 8dBi, 858-878MHz ](https://botland.store/antennas/20121-antenna-lora-fiberglass-8dbi-858-878mhz-lenght-130cm-seeedstudio-318020611-5904422362737.html)
- [MikroTik 868_Omni_antenna](https://wifi-anteny.heureka.sk/mikrotik-868-omni-antenna/#prehlad/)

---

## 🛡️ Filtre

V mestskom prostredí je veľa rušenia (napr. BTS základňové stanice). Použitie filtrov SAW / dutinkové / cavity filtre pre 868 MHz pásmo výrazne [pomáha](https://pytlicek.github.io/hamradio/filters/index.html):  

- [SAW filter BPF-868MHz](https://www.laskakit.cz/saw-filter-bpf-868mhz/)
- [AliExpress Dutinkovy 868](https://www.aliexpress.com/item/1005006356979446.html)
