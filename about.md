# Čo je MeshCore

**MeshCore je sieť na posielanie textových správ, ktorá funguje bez internetu, bez mobilného signálu a bez akéhokoľvek poskytovateľa.** Namiesto toho dobrovole budovaná ifraštruktúra používa malé vačsinou solárne rádiá v pásme 868 MHz, ktoré preposielajú medzi sebou vaše správy

Predstavte si to ako SMS-ky, ktoré nejdú cez operátora, ale skáču z rádia na rádio - preskočia strechu, kopec, mesto - a doručia sa aj v prípade že vypadne mobilná sieť alebo internet.

Prakticky to znamená:
- **Nepotrebujete SIM kartu, dáta ani paušál.** Sieť je zadarmo a patrí komunite, ktorá ju stavia.
- **Nepotrebujete rádioamatérsku licenciu.** Beží v [ISM pásme](./glossary.md#ism "Voľné rádiové pásmo (u nás 868/869 MHz), ktoré smie používať ktokoľvek bez licencie"), ktoré smie používať ktokoľvek.
- Ako „displej a klávesnicu“ použijete svoj mobil - malé rádio sa k nemu pripojí cez Bluetooth. Existujú však aj **samostatné zariadenia s vlastným displejom a klávesnicou**, ktoré mobil vôbec nepotrebujú.

## Prečo MeshCore vznikol

MeshCore vytvoril koncom roka 2024 Austrálčan **Scott Powell** (projekt Ripple Radios). Firmware rádia je **open source** pod licenciou MIT, čiže zadarmo a otvorené každému.

MeshCore to rieši **rozdelením rolí**:

> **Správy preposielajú len opakovače ([repeatre](./glossary.md#repeater "Zariadenie, ktoré len počúva a preposiela správy ďalej - kostra siete")).**

Vďaka tomu môže do siete pribudnúť aj sto nových ľudí a záťaž na éteri sa prakticky nezmení. Kapacita siete rastie len vtedy, keď niekto vedome postaví nový repeater na dobrom mieste. To je celá filozofia MeshCore - a dôvod, prečo naša sieť dokáže rásť aj cez tri krajiny.

## Ako to funguje

MeshCore stojí na rádiovej technológii **[LoRa](./glossary.md#lora "Rádiová technológia na veľký dosah a nízku spotrebu - ale s veľmi malou prenosovou rýchlosťou")**. Tá vie preniesť len veľmi málo dát (rádovo stovky bitov za sekundu), ale zato veľmi ďaleko a s minimálnou spotrebou - pri priamej viditeľnosti bežne aj desiatky kilometrov. Preto sa cez ňu posielajú **len krátke textové správy** - žiadne fotky, hlas ani súbory. Podrobnejšie o týchto limitoch a o tom, ako sa v sieti správať ohľaduplne, píšeme v [meshtiquette](./meshtiquette.md).

Zvyšok je o tom, čím tie správy píšete a ako si nájdu cestu k adresátovi.

### 1. Čím to obsluhujete

Máte dve možnosti, ako správy písať a čítať:

**a) Rádio + mobil (najbežnejšie).** Vaše rádio zariadenie má v sebe firmware **[Companion](./glossary.md#companion "Firmware pre bežného užívateľa - rádio pripojené k mobilu, ktoré nepreposiela cudzie správy")** a k mobilu sa pripojí cez Bluetooth. Písanie a čítanie prebieha v aplikácii MeshCore ([Android](https://play.google.com/store/apps/details?id=com.liamcottle.meshcore.android) \| [iOS](https://apps.apple.com/nz/app/meshcore/id6742354151)) na telefóne, samotný prenos zabezpečuje rádio. Rovnako sa dá pripojiť aj k počítaču.

**b) Samostatné (standalone) zariadenie.** Existujú aj zariadenia, ktoré majú **vlastný displej a klávesnicu** - napríklad [LilyGo T-Deck Plus](./hardware.md#vhodné-ako-klient). Po naflashovaní samostatného firmvéru fungujú úplne bez mobilu a bez počítača: zapnete ich, píšete priamo na nich a fungujú ako malý off-grid komunikátor. Hodí sa to práve pre núdzové situácie, kde nechcete závisieť od telefónu a jeho batérie.

Obe možnosti sú v tej istej sieti a navzájom si normálne píšu - je to len otázka toho, čo vám viac vyhovuje.

### 2. Repeatre držia sieť pokope

**Repeater** (opakovač) je zariadenie na streche, kopci alebo stožiari, ktoré preposiela správy. Väčšinou beží na solárnom paneli a batérii, takže funguje aj bez elektriny. Práve repeatre vytvárajú pokrytie: každý skok cez repeater ([„hop“](./glossary.md#hop "Jedno preposlanie správy cez jeden repeater")) posunie správu o kus ďalej.

Ak chcete pomôcť sieti rásť, [postavte repeater](./repeater.md).

### 3. Ako si správa nájde cestu

Toto je hlavný trik MeshCore. Funguje v dvoch režimoch:

- **[Flood (záplava)](./glossary.md#flood "Režim, v ktorom správu preposielajú všetky repeatre, ktoré ju počujú")** - správa sa pustí do siete „naslepo“ a preposielajú ju všetky repeatre, ktoré ju počujú. Takto ide **každá správa do kanála alebo skupiny** a takto ide aj **prvá priama správa** novému kontaktu - inak sa cesta k nemu nedá zistiť. Cenou za to je [vysielací čas](./glossary.md#airtime "Ako dlho zariadenie fyzicky obsadzuje éter jednou správou - zdieľaný a vzácny zdroj") celej siete.
- **[Direct (priama cesta)](./glossary.md#direct "Režim, v ktorom správa ide po vopred známej ceste cez konkrétne repeatre")** - z doručenky sa vaše zariadenie dozvie, **cez ktoré konkrétne repeatre** správa prešla. Túto cestu si zapamätá a všetky ďalšie správy pošle už len po nej. Ostatné repeatre v sieti sa vtedy vôbec nemusia ozvať.

Ak sa cesta pokazí (repeater vypadne, zmeníte polohu), zariadenie sa automaticky vráti k flood režimu a nájde si novú cestu. Cesta sa tak sama vie opraviť.

### 4. Adverty - ako sa uzly navzájom nájdu

Aby ste vôbec vedeli, že niekto v sieti existuje, zariadenia občas vyšlú **[advert](./glossary.md#advert "Vizitka uzla - meno, verejný kľúč a prípadne poloha")** - vizitku so svojím menom, verejným kľúčom a prípadne polohou. Práve z advertov sa vám v aplikácii plnia kontakty.

Adverty sú dvojaké: **[flood advert](./glossary.md#flood-advert "Advert, ktorý sa rozšíri celou sieťou cez všetky repeatre")** sa rozšíri celou sieťou, **[zero-hop advert](./glossary.md#zero-hop-advert "Advert, ktorý sa nepreposiela - počujú ho len zariadenia priamo na dosah")** počujú len tí, ktorí sú priamo na dosah.

### 5. Regióny - aby sa všetko nešírilo všade

Slovenská sieť je prepojená s Maďarskom a Rakúskom. Bolo by zbytočné plytvanie [vysielacieho času](./glossary.md#airtime "Ako dlho zariadenie fyzicky obsadzuje éter jednou správou - zdieľaný a vzácny zdroj"), ak by sa správa z košického kanála opakovala až vo Viedni. Preto má MeshCore **[regióny (angl. region scope)](./glossary.md#region "Nálepka na flood prevádzke, ktorá určuje, kde je správa relevantná")**: správa dostane nálepku, napr. `sk-ke`, a preposielajú ju len repeatre, ktoré majú tento región nastavený.

Návod na nastavenie regiónov nájdete v [zozname kanálov](./channels.md#ako-pridať-a-nastaviť-región).

### 6. Súkromie

[Priame správy](./glossary.md#dm "Správa jednému príjemcovi, šifrovaná end-to-end") sú **šifrované end-to-end**. Repeatre, cez ktoré správa preteká, vidia len to, kam ju majú poslať ďalej - obsah prečítať nedokážu. Skupinové kanály sú chránené zdieľaným kľúčom: kto ho nemá, nevie prečítať správu. Pozor - hašhtag kanály sa dajú ľahko uhádnuť, preto ich nepovažujeme za súkromné kanály.

## Čo MeshCore je

- **Núdzová komunikácia** - keď vypadne prúd, mobilná sieť alebo internet.
- **Miesta bez signálu** - hory, chaty, jaskyne, terénne akcie.
- **Hobby a experiment** - rádiá, antény, solár, dosah. Pre mnohých je to hlavné lákadlo.
- **Komunita** - lokálne kanály, na ktorých sa dá jednoducho ozvať susedom v regióne.

## Čo MeshCore nie je

Aby nevznikli falošné očakávania:

- **Nie je to náhrada internetu.** Žiadny web, žiadne fotky, žiadne volanie.
- **Nie je to telemetrická sieť.** Každé pravideľné automatizované vysielanie telemetrie spôsobuje postupné zahltenie [vysielacieho času](./glossary.md#airtime "Ako dlho zariadenie fyzicky obsadzuje éter jednou správou - zdieľaný a vzácny zdroj"), ktorý zdieľajú všetci. Na priebežné meranie teplôt, trackery a pod. je vhodnejší LoRaWAN alebo vlastná neverjená sieť na inej frekvencii.
- **Nie je to rýchle.** Správa môže cestovať aj niekoľko sekúnd, hlavne cez viac skokov.
- **Nie je to garantovaná služba.** Sieť je zadarmo, stavia komunita vo voľnom čase, repeatre občas vypadnú.
- **Nie je to anonymná sieť.** Obsah je síce šifrovaný, ale vaše zariadenie sa v éteri ohlasuje svojím menom a kľúčom a dá sa čiastočne vystopovať podľa zaznamenaných ciest

---

## Ako začať

1. Vyberte si [zariadenie](./hardware.md).
2. Naflashujte doň firmware cez [MeshCore Flasher](https://flasher.meshcore.io) - pri bežnom rádiu voľbu **Companion radio Bluetooth**, pri zariadení s vlastnou klávesnicou a displejom samostatný (standalone) firmware pre daný model.
3. Ak používate Companion, nainštalujte si mobilnú aplikáciu ([Android](https://play.google.com/store/apps/details?id=com.liamcottle.meshcore.android) \| [iOS](https://apps.apple.com/nz/app/meshcore/id6742354151)). Nastavte si ju podľa [odporúčaných nastavení](./settings.md).
4. Pridajte si [kanály](./channels.md) a nezabudnite na regióny.
5. Prečítajte si [meshtiquette](./meshtiquette.md) a ozvite sa nám na [Discorde](https://discord.gg/Zx5JuhszUb).

Nerozumiete niektorému pojmu? Pozrite si [slovník pojmov](./glossary.md).
