# Repeatre
## Stavba Repeatra - Hardware

Ak má mať mesh sieť v meste dlhodobý zmysel, treba sa zamerať na **energetickú efektivitu** a **odolnosť voči rušeniu**. Zariadenia s **nRF52** čipsetmi (RAK dosky alebo Seeed Xiao) majú nižšiu spotrebu a tým pádom vydržia dlhšie na solárnom napájaní. Pridaním kvalitného solárneho panelu, dostatočnej batérie a dobrej antény získame repeater, ktorý funguje stabilne aj v zimných mesiacoch (kompletne bez potreby výmeny batérií).

Neodmysliteľnou súčasťou buildov sú **filtre** – bez nich bude v mestskom prostredí sieť zahltená rušením zo silných BTS alebo iných zariadení. SAW alebo cavity filtre na 868 MHz znižujú šum a umožnia, aby repeater prijímal a odosielal správy čisto. Rovnako dôležité je použiť anténu s vhodným ziskom a pred samotnou inštaláciou preveriť pásmo cez **SDR meranie**, aby bolo jasné, či lokalita nie je zahltená. Pri umiestnení blízko BTS je nutné anténu orientovať a filtrovať tak, aby sa navzájom nerušili.

---

### SenseCAP Solar Repeater
- **Rádio + Solárny panel + Baterky:** [Seeed SenseCAP P1 Pro](https://www.seeedstudio.com/SenseCAP-Solar-Node-P1-Pro-for-Meshtastic-LoRa-p-6412.html)
- **Redukcia RP-SMA -> SMA:** [GOLDEN LOCH SMA - RPSMA Z/RV 50R redukcia](https://www.gme.sk/v/1500900/golden-loch-sma-rpsma-z-rv-50r-redukcia)
- **Filter:** [SAW BPF 868Mhz](https://www.aliexpress.com/item/1005007528774067.html) \| [alternatívny predajca 1](https://www.aliexpress.com/item/1005009107800288.html) \| [alternatívny predajca 2](https://www.aliexpress.com/item/1005008455588388.html)
- **Samovulkanizačná páska:** [EMOS 19mm/10m](https://www.cbelektro.sk/izolacna-paska-samovulkanizacna-19mm-10m-cierna-emos-p264892)
- **Anténa:** [MikroTik Omni 868 MHz 6.5 dBi](https://wifi-anteny.heureka.sk/mikrotik-868-omni-antenna/)

---

### Urob-si-sám Repeater
- **Rádio:** [RAK 4631](https://www.aliexpress.com/item/1005006901039995.html)
- **Solárny panel:** [Soshine 6V/6W](https://www.fotoextra.cz/soshine-mini-solar-panel-6v-6w.html)
- **Baterka:** [Li-Pol 10000 mAh (protected)](https://techfun.sk/produkt/li-pol-bateria-kablik-ochranny-obvod/?attribute_pa_bateria=1260110-10000-mah)
- **Filter:** [SAW BPF 868Mhz](https://www.aliexpress.com/item/1005007528774067.html) \| [alternatívny predajca 1](https://www.aliexpress.com/item/1005009107800288.html) \| [alternatívny predajca 2](https://www.aliexpress.com/item/1005008455588388.html)
- **Krabica:** [U-01-18](https://www.gme.sk/v/1511573/u-01-18-instalacna-krabica)
- **Prechodky (2x):** [M16*1.5 IP68](https://techfun.sk/produkt/prechodky-pre-kable-biele-rozne-velkosti-ip68/?attribute_pa_variant=m161-5)
- **Samovulkanizačná páska:** [EMOS 19mm/10m](https://www.cbelektro.sk/izolacna-paska-samovulkanizacna-19mm-10m-cierna-emos-p264892)
- **Anténa:** [MikroTik Omni 868 MHz 6.5 dBi](https://wifi-anteny.heureka.sk/mikrotik-868-omni-antenna/)

---

<table style="width:100%; border-collapse:collapse; text-align:center;">
  <tr>
    <td style="width:60%; padding:4px;">
      <img src="img/XIAO_Solar_Repeater.jpg" alt="SenseCap Repeater" style="width:100%; height:350px; object-fit:cover;"/>
    </td>
    <td style="width:40%; padding:4px;">
      <img src="img/DiY_Solar_Repeater.jpg" alt="DiY Repeater" style="width:100%; height:350px; object-fit:cover;"/>
    </td>
  </tr>
  <tr>
    <td>SenseCAP Solar Node P1</td>
    <td>DIY Repeater</td>
  </tr>
</table>

---

Pozrite tiež: [Nastavenia repeatra](./settings.md#repeatre)