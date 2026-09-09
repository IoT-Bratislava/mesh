# Slovník pojmov

V MeshCore sa používa dosť anglických výrazov, ktoré sa do slovenčiny neprekladajú alebo sa prekladajú nejednotne. Tu je prehľad toho, na čo narazíte v aplikácii, na Discorde aj na tejto stránke.

Ak hľadáte skôr celkový obraz - čo MeshCore je a ako funguje - začnite radšej stránkou [Čo je MeshCore](./about.md).

---

## Základné pojmy

<a id="lora"></a>**LoRa** *(Long Range)*
Rádiová technológia na prenos malého množstva dát na veľkú vzdialenosť s minimálnou spotrebou. Základ celej siete. Je pomalá - rádovo stovky bitov až jednotky kbps - preto sa cez ňu posielajú len krátke textové správy.

<a id="mesh"></a>**Mesh (sieť)**
Sieť bez centra, v ktorej si zariadenia správy navzájom preposielajú. Nemá server, ktorý by sa dal vypnúť.

<a id="uzol"></a>**Uzol / Node**
Akékoľvek zariadenie v sieti - klient, repeater aj room server.

**MeshCore**
Sieť a Firmware (softvér v rádiu) + aplikácie, ktoré túto sieť tvoria.

<a id="meshtastic"></a>**Meshtastic**
Starší a rozšírenejší konkurenčný projekt na rovnakom hardvéri. Hlavný rozdiel: v Meshtastic preposiela správy každé zariadenie, v MeshCore len repeatre. Zariadenie môže bežať buď na jednom, alebo na druhom - nie na oboch naraz.

<a id="ism"></a>**ISM pásmo**
Voľné rádiové pásmo, ktoré smie používať ktokoľvek bez licencie. U nás ide o pásmo okolo **868 MHz**.

**Firmware**
Program nahratý priamo v rádiu. Podľa toho, ktorý firmware nahráte, sa zo zariadenia stane klient, repeater alebo room server.

**Flasher / flashovanie**
Nahratie firmvéru do zariadenia. Robí sa cez [flasher.meshcore.io](https://flasher.meshcore.io) v prehliadači, so zariadením pripojeným USB káblom.

---

## Role zariadení

<a id="companion"></a>**Companion / Companion Radio**
Firmware pre bežného užívateľa. Rádio sa cez Bluetooth (alebo USB) pripojí k mobilu či počítaču a slúži ako „modem“ - písanie prebieha v aplikácii. **Companion nikdy nepreposiela cudzie správy.**

**Klient / Client**
Bežný užívateľ siete, teda zariadenie s firmvérom Companion. V praxi sa slová „klient“ a „companion“ používajú zameniteľne.

<a id="repeater"></a>**Repeater / Opakovač**
Zariadenie, ktoré len počúva a preposiela správy ďalej - typicky na streche, kopci alebo stožiari, často na solárnom paneli. Repeatre sú jediné, čo v MeshCore preposiela prevádzku, takže tvoria kostru siete. [Ako postaviť repeater](./repeater.md)

<a id="room-server"></a>**Room Server**
Niečo ako nástenka s pamäťou: uchová správy pre užívateľov, ktorí neboli online, a tí si ich vyzdvihnú neskôr (podobne ako e-mail). Bežný kanál nič neuchováva - ak používateľ nemá zapnuté rádio v momente ako správa posiela vrámci siete, správu neskôr nedostane.

---

## Sieť a smerovanie

<a id="packet"></a>**Paket / Packet**
Základná jednotka, ktorú rádio vysiela do éteru. **Nie každý paket je správa** - paketom je aj advert, potvrdenie (ACK), hľadanie cesty, telemetria či príkaz repeatru. Väčšina prevádzky v sieti sú práve takéto servisné pakety, nie text od ľudí. Repeatre preposielajú pakety, nie správy - preto sa všetko, čo sieť zaťažuje, počíta v paketoch a vysielacom čase. Do jedného paketu sa zmestí len obmedzené množstvo dát (rádovo stovky bajtov).

<a id="advert"></a>**Advert**
„Vizitka“, ktorú zariadenie občas vyšle do siete - obsahuje meno, verejný kľúč a prípadne polohu. Vďaka advertom sa vám v aplikácii objavujú kontakty.

<a id="flood-advert"></a>**Flood advert**
Advert, ktorý sa rozšíri celou sieťou cez všetky repeatre. Je drahý na vysielací čas, preto sa má posielať zriedkavo - u nás na repeatroch odporúčame interval **47 hodín**.

<a id="zero-hop-advert"></a>**Zero-hop advert**
Advert, ktorý sa nepreposiela - počujú ho len zariadenia priamo na dosah. Užitočný na zdielanie svojho kontaktu lokálne

<a id="flood"></a>**Flood (záplavové smerovanie)**
Režim, v ktorom správu/packet preposielajú všetky repeatre, ktoré ju počujú. Používa sa pri prvom kontakte, pri hľadaní cesty a pri kanáloch. Spoľahlivé, ale zaťažujúce.

<a id="direct"></a>**Direct (priame smerovanie)**
Režim, v ktorom správa ide po vopred známej ceste cez konkrétne repeatre. Po prvom úspešnom kontakte sa MeshCore prepne naň a šetrí tým éter celej sieti. **Platí len pre priame správy (DM) a správcovské (management) pakety** (prihlásenie k repeatru, vzdialená správa, telemetria). **Správy do kanálov a skupín idú vždy flood režimom** keďže nemajú jedného konkrétneho adresáta.

<a id="path"></a>**Path / Cesta**
Zoznam repeatrov, cez ktoré správa prešla. Pri priamych správach si ho zariadenie zapamätá a použije pri ďalšej komunikácii; ak cesta prestane fungovať, vráti sa k flood režimu a nájde novú.
Cestu majú aj flood pakety - vidíte teda, kadiaľ prišla správa z kanála - ale **pri kanáloch a skupinách sa nedá nastaviť ani použiť na ďalšie posielanie**, pretože tie idú vždy flood režimom. Slúži tam len na informáciu a diagnostiku.

<a id="hop"></a>**Hop / Skok**
Jedno preposlanie správy cez jeden repeater. „3 hopy“ znamená, že správa prešla cez tri repeatre.

**Path hash / Hash trasy**
Koľko bajtov sa použije na identifikáciu každého repeatra v ceste. Väčší hash = menšia šanca zámeny dvoch repeatrov, ale menej možných skokov (1 bajt = 64 skokov, 2 bajty = 32, 3 bajty = 21). U nás odporúčame **2 bajty**.

<a id="ack"></a>**ACK / Potvrdenie**
Potvrdenie, že správa dorazila adresátovi. V aplikácii sa prejaví ako „doručené“. Z ACK sa zároveň dozvieme, ktorou cestou správa išla.

<a id="region"></a>**Region / Region scope / Scope**
Nálepka pripojená k flood prevádzke, ktorá určuje, kde je správa relevantná (napr. `sk`, `sk-ba`, `sk-ke`). Preposielajú ju len repeatre, ktoré daný región poznajú - vďaka tomu sa správa z Bratislavy nešíri po celej strednej Európe. Nastavovaniu regiónov sa hovorí aj **scopovanie**. [Ako nastaviť región](./channels.md#ako-pridať-a-nastaviť-región)

**Global región (`*`)**
Zástupný región pre prevádzku bez nálepky. Ak ho repeater nemá povolený, prestane preposielať neregionálnu flood prevádzku (adverty a pod.), takže sa vypína len vedome a s rozvahou.

**Loop detection**
Ochrana proti tomu, aby správa krúžila v sieti dokola medzi tými istými repeatrami.

**Neighbours / Susedia**
Funkcia repeatra, ktorá vypíše susedné uzly, od ktorých priamo počula advert, spolu s kvalitou signálu (SNR). Používa sa na diagnostiku: kam až repeater reálne dovidí a ako kvalitné je spojenie s jednotlivými susedmi. Hodí sa pri ladení antény, hľadaní zdroja rušenia aj pri posudzovaní nového stanovišťa.

**Discover nearby nodes**
Funkcia v aplikácii (*Tools*), ktorou zistíte, ktoré uzly sú vo vašom priamom dosahu. Používajte ju namiesto posielania „ping“ a „test“ správ do kanálov.

**Verejný / súkromný kľúč**
Identita zariadenia. Verejný kľúč sa šíri v advertoch a slúži na šifrovanie a overenie odosielateľa, súkromný ostáva v zariadení. Ak stratíte **súkromný kľúč**, stratíte aj identitu uzla - ostatní vás budú vidieť ako nový kontakt - preto sa oplatí ho zálohovať.

**Prefix / ID**
Začiatok verejného kľúča, používaný na rýchlu identifikáciu uzla v ceste. Býva to prvý bajt, ale podľa nastavenia **hashu trasy** (viď nižšie) môže mať aj viac bajtov - čím dlhší prefix, tým menšia šanca, že sa dva uzly zamenia.

**Kolízia ID**
Situácia, keď dva uzly majú rovnaký prefix. Smerovanie funguje ďalej, ale sťažuje to určenie, kadiaľ správa išla. Rieši sa vygenerovaním nového kľúča s voľným prefixom. [Návod](./settings.md#kolízie-id)

**Kontakt**
Uzol uložený vo vašej aplikácii - companion, repeater alebo room server. Pridáva sa automaticky z prijatých advertov alebo manuálne. Aby sa vám zoznam zbytočne nezaplnil, pozrite si [odporúčané nastavenia kontaktov](./settings.md#nastavenia-kontaktov).

---

## Kanály a správy

<a id="kanal"></a>**Kanál / Channel**
Skupinová konverzácia. Každý, kto má kľúč kanála, ho vidí a môže doň písať. Kanály sú „živé“ - neuchovávajú históriu pre tých, ktorí boli offline.

**Public**
Predvolený kanál, ktorý má každý. U nás je medzinárodný a komunikuje sa na ňom po anglicky.

<a id="hashtag-kanal"></a>**Hashtag kanál**
Kanál, ktorého kľúč sa odvodí priamo z jeho názvu (napr. `#slovakia`). Netreba si nikde vymieňať heslá - stačí zadať rovnaký názov. [Zoznam kanálov](./channels.md)

**Secret / Kľúč kanála**
Zdieľaný kľúč, ktorým je kanál šifrovaný. Kto ho nemá, nevidí obsah.

<a id="dm"></a>**DM / Priama správa**
Správa jednému konkrétnemu príjemcovi, šifrovaná end-to-end. Repeatre po ceste jej obsah neprečítajú.

---

## Rádio a nastavenia

**Frekvencia**
Na ktorej frekvencii sieť beží. Slovensko: **869.618 MHz**. Kto ju má nastavenú inak, sieť nepočuje.

**Bandwidth / Šírka pásma**
Šírka použitého kanála v kHz. Slovensko: **62.5 kHz**. Širší kanál = rýchlejší prenos, ale menší dosah a väčšia citlivosť na rušenie.

**Spreading Factor (SF)**
Miera „roztiahnutia“ signálu. Vyššie SF = väčší dosah, ale výrazne pomalší prenos a dlhší vysielací čas. Slovensko: **SF 7**.

**Coding Rate (CR)**
Množstvo pridanej korekcie chýb. Nižšie CR = kratší vysielací čas, vyššie = väčšia odolnosť voči chybám. Slovensko: **5**.

**Preset**
Uložená kombinácia frekvencie, šírky pásma, SF a CR. Naša sieť používa preset **Slovakia**. Všetky štyri hodnoty musia sedieť, inak sa nedopíšete. [Odporúčané nastavenia](./settings.md)

<a id="airtime"></a>**Airtime / Vysielací čas**
Ako dlho zariadenie fyzicky obsadzuje éter jedným paketom. Je to zdieľaný a vzácny zdroj - preto všetky odporúčania na jeho šetrenie nájdete na stránke [meshtiquette](./meshtiquette.md)

<a id="snr"></a>**SNR**
Odstup signálu od šumu v dB. Hovorí, o koľko je prijatý signál silnejší než šum na pozadí. Čím vyššie, tým lepšie - a špecialita LoRa je, že prijíma aj hlboko pod úrovňou šumu, teda pri záporných hodnotách. Orientačne pri našom nastavení (SF 7):
- **nad +5 dB** - výborné, veľmi stabilné spojenie
- **0 až +5 dB** - dobré
- **-5 až 0 dB** - slabšie, menej odolné voči rušeniu
- **pod -7 dB** - veľmi slabé hraničné spojenie

**RSSI**
Absolútna sila prijatého signálu v dBm (napr. -110 dBm). Sama o sebe menej vypovedá než SNR - v zarušenom prostredí môže byť silný signál aj tak nečitateľný.

**Zisk antény (dBi)**
Koľko z vyžiareného výkonu anténa „sústredí“ do požadovaného smeru. Vyšší zisk u všesmerovej antény znamená plochší lalok - lepší dosah do diaľky, horší do kopca nad sebou.

**Line of Sight / Priama viditeľnosť**
Nič neprekáža medzi dvoma anténami. Pre LoRa na 868 MHz je to kľúčové - kopec alebo panelák dokáže spojenie zabiť. V aplikácii je na to nástroj *Tools → Line of Sight*.

<a id="filter"></a>**SAW / cavity filter**
Rádiový filter, ktorý prepustí len pásmo 868 MHz a odreže rušenie od okolitých vysielačov (napr. mobilných BTS). V meste prakticky povinná výbava repeatra. [Odporúčané filtre](./hardware.md)

**SDR**
Softvérovo definované rádio - lacný USB prijímač, ktorým sa dá pred inštaláciou repeatra premerať, aké je na danom mieste rušenie.

---

## Správa a údržba repeatra

**CLI / Command Line**
Textový príkazový riadok repeatra, dostupný cez USB, alebo diaľkový manažment.

**Remote admin / Prihlásenie k repeatru**
Pripojenie k repeatru na diaľku cez MeshCore sieť pomocou administrátorského hesla - dá sa tak meniť nastavenie bez toho, aby ste mali fyzický prístup k repeatru.

**Guest heslo**
Heslo pre hosťovský prístup k repeatru, ktorý dovolí pozrieť štatistiky, susedov a Owner Info, ale nie meniť nastavenia. Odporúčame nechať ho prázdne, teda prístup voľný.

**Owner Info**
Textové pole s kontaktom na majiteľa repeatra. Vyplňte ho - vďaka nemu sa dá koordinovať, keď sa v sieti niečo mení alebo pokazí.

**OTA** *(Over The Air)*
Aktualizácia firmvéru na diaľku - cez Bluetooth (nRF52) alebo WiFi (ESP32), bez potreby fyzicky sa dostať k zariadeniu. [Návod](./settings.md#aktualizácie-firmware-cez-bluetoothwifi)

**Bootloader**
Malý program, ktorý sa v zariadení spúšťa ako prvý a stará sa o načítanie firmvéru a jeho aktualizáciu. Pred prvou OTA aktualizáciou nRF52 zariadenia odporúčame aktualizovať ho na verziu **OTAFIX** - [postup nájdete v návode na OTA](./settings.md#ota-pre-nrf52-bluetooth), samotný bootloader je na [stránke OTAFIX](https://github.com/oltaco/Adafruit_nRF52_Bootloader_OTAFIX/releases).

---

Chýba vám tu nejaký pojem? Napíšte nám na [Discorde](https://discord.gg/Zx5JuhszUb) alebo [e-mailom](mailto:recrof@gmail.com?subject=MeshCore%20slovnik).
