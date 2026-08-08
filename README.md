# MeshCore Sieť na Slovensku 🇸🇰

<div style="border-left: 4px solid #d29922; background: #fff8e6; padding: 12px 16px; border-radius: 4px;">
  <h2>⚠️ Upozornenie</h2>
  Od <strong>8.8.2026</strong> prešla sieť na nové nastavenia nekompatibilné s doterajšími a <strong>je potrebné preladiť všetky zariadenia</strong>.<br>

  <ul>
    <li>Preset: <strong>Slovakia</strong></li>
    <li>Frekvencia (MHz): <strong>869.618 MHz</strong></li>
    <li>Šírka pásma: <strong>62.5 kHz</strong></li>
    <li>Spreading Factor(SF):  <strong>7</strong></li>
    <li>Coding Rate(CR): <strong>5</strong></li>
  </ul>

  <h3>Ak máte repeater</h3>
  <span>Môžete použiť príkaz v príkazovom riadku:</span><br>
  <code>set radio 869.618,62.5,7,5</code><br>
  <span>a potom</span><br>
  <code>reboot</code><br>
  <span>dalej prosím <a href="https://docs.google.com/spreadsheets/d/1YoGlBNesV491CifETy-dg088rg9RRBDwJvzPoMUT2YQ/edit">zapíšte svoj repeater do hárku.</a></span>
  <br>
  <span>Viac k téme sa dočítate na našom Discorde - kanál <a href="https://discord.com/channels/1456042561016692843/1516150102035529869">#migracie</a></span>

</div>

## Základné informácie
- Siet MeshCore bola primárne budovaná na núdzovú textovú komunikáciu
- Je určená pre všetkých, na prevádzku LoRa mesh zariadení v ISM pásme **nie je potrebné mať rádioamatérsku licenciu**.
- Prosím prečítajte si ,,[meshtiquette](./meshtiquette.md)'', kde rozoberáme technologické limity siete a odporúčame ako sieť používať efektívne

### Ako prejsť na MeshCore
1. Pripojte vaše [zariadenie](./hardware.md) cez USB k počítaču.
2. Otvorte [MeshCore Flasher](https://flasher.meshcore.io) a nahrajte **Companion radio Bluetooth** firmware.
3. Do mobilu nainštalujte aplikáciu:
  - [MeshCore pre Android](https://play.google.com/store/apps/details?id=com.liamcottle.meshcore.android)
  - [MeshCore pre iOS](https://apps.apple.com/us/app/meshcore/id6742354151)

### Nastavenia, Zariadenia, Návody
- [Kanály](./channels.md)
- [Odporúčané nastavenia](./settings.md)
- [Odporúčané zariadenia](./hardware.md)
- [Ako postaviť Repeater](./repeater.md)

### Stretnutia
- **Stretávame sa každý štvrtok o 17:30** v Bratislave, Rádioklube **Omega (OM5M / OM3KFF)**.
- Adresa: Staré Grunty 53 v Mlynskej doline, bloky A/B. Je to tá budova s veľkými anténami na streche
- Web: [https://om3kff.sk/?lang=sk](https://om3kff.sk/?lang=sk)
<br><img src="https://om3kff.sk/wp-content/uploads/2013/03/mapa_pristup2_small.gif" alt="pristup" style="width:100%; max-width:500px; object-fit:cover;"/>

### Diskusia, koordinácia
- [MeshCore-SK Discord](https://discord.gg/Zx5JuhszUb)

### Ďalšie zdroje
- [Živá mapa siete](https://map.meshcore.hu)
- [Video návod (EN)](https://www.youtube.com/watch?v=iaFltojJrAc&list=PLshzThxhw4O5UniQfTVEQbaZ3tePF9iCc)
- [Využitie mesh sietí v A.R.E.S (Amateur Radio Emergency Service)](https://aresom.wordpress.com/lora-mesh-siete-pre-tiesnovu-komunikaciu-siete-meshtastic-a-meshcore-na-slovensku/)
- [Email Kontakt](mailto:recrof@gmail.com?subject=MeshCore%20Výzva)
- [Užitočné odkazy](./links.md)
