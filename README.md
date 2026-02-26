# 🛜 MeshCore Sieť na Slovensku / MeshCore in Slovakia

## 💡 Informácie o MeshCore na Slovensku
Na Slovensku už niekoľko mesiacov komunita prevádzkuje **MeshCore** sieť, ktorá nahradila pôvodný Meshtastic.
Na prevádzku LoRa mesh zariadení v ISM (industrial, Scientific, and Medical - celosvetovo) **nieje potrebné mať 📻 Rádioamatérsku licenciu** 👍.

### Výhody MeshCore oproti Meshtasticu
- Spoľahlivejšie doručovanie správ
- Odolnejšie routovanie správ
- Menšie zahltenie siete telemetriou

### Frekvencia / Modulacia
<span style="color: red">Od 7. 9. 2025 používame parametre modulácie (MeshCore radio settings):</span>

- Preset: **EU/UK (Narrow) - 869.618MHz / SF8 / BW62.5 / CR8**
- Frequency (MHz): **869.618 MHz**
- Bandwidth: **62.5 kHz**
- Spreading Factor:  **8**
- Coding Rate: **5**

Tieto parametre oproti predvolenému presetu **EU/UK (Long Range)** zúžia bandwidth a posúvajú frekvenciu čo sa prejaví v menšom zarušení a vyššej spolahlivosti.

### Kanály ktoré používame
Kedže sme prepojení s Madarskom a Rakúskom, Public kanál je medzinárodny kanál a každá krajina má svoj národný Hashtag kanál.
Hashtag kanály sa dajú pridat v Hlavnom menu -> Add channel -> Join Hashtag channel
- **Public** - Predvolnený kanál, na ktorom komunikujeme v angličtine
- **#slovakia** - Slovenský národný Hashtag kanál
- **#hungary** - Madarský národný Hashtag kanál
- **#austria** - Rakúsky národný Hashtag kanál

### 📻 📡 Odporúčané zariadenia
[👉 Odporúčané zariadenia](./hardware.md)
[👉 Ako na Repeater: HW/Konfiguracia/Info](./repeater.md)

### Ako prejsť na MeshCore?
1. Pripojte vaše Meshtastic zariadenie cez USB k počítaču.
2. Otvorte [MeshCore Flasher](https://flasher.meshcore.dev) a nahrajte **Companion radio Bluetooth firmware**.
3. Do mobilu nainštalujte aplikáciu:
  - [MeshCore pre Android](https://play.google.com/store/apps/details?id=com.liamcottle.meshcore.android)
  - [MeshCore pre iOS](https://apps.apple.com/us/app/meshcore/id6742354151)

### Zapojenie a pomoc
- Ak chcete byť používateľ siete: stačí nahrať firmware a používať aplikáciu.
- Ak chcete pomôcť rozšíriť sieť a máte vhodné miesto pre repeater, ozvite sa nám. Radi pomôžeme s inštaláciou.

### Diskusia, koordinácia
1. [MeshCore Discord pozvánka](https://discord.gg/PwAMdThdXp)
2. [Regionálny thread Slovakia](https://discord.com/channels/1343693475589263471/1345309961315680348)

### Stretnutia
- **Stretávame sa každý štvrtok o 17:30** v Bratislave, Rádioklube **Omega (OM5M / OM3KFF)**.
- Adresa: Staré Grunty 53 v Mlynskej doline, bloky A/B. Je to tá budova s veľkými anténami na streche
- Web: [https://om3kff.sk/?lang=sk](https://om3kff.sk/?lang=sk)
  <img src="https://om3kff.sk/wp-content/uploads/2013/03/mapa_pristup2_small.gif" alt="pristup" style="width:100%; height:350px; object-fit:cover;"/>

### Ďalšie zdroje
- Video návod (EN): [YouTube](https://www.youtube.com/watch?v=t1qne8uJBAc)
- Živá mapa siete: [MeshCore Map](https://map.mc868.hu)
- [Využitie mesh sietí v A.R.E.S (Amateur Radio Emergency Service)](https://aresom.wordpress.com/lora-mesh-siete-pre-tiesnovu-komunikaciu-siete-meshtastic-a-meshcore-na-slovensku/)
- Email Kontakt: recrof@gmail.com (predmet: *MeshCore Vyzva*)
- Užitočné odkazy: [links.md](./links.md)
