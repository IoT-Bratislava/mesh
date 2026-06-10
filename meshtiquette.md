### Ako sieť funguje a prečo na tom záleží

MeshCore je mesh sieť postavená na LoRa rádiách, kde uzly (nodes) preposielajú správy cez viacero skokov (multi-hop) a tým rozširujú dosah bez potreby infraštruktúry. Aby sieť dlhodobo dobre fungovala, je dobré rozumieť jej prirodzeným limitom — a podľa toho sa správať. Nejde o pravidlá, ale o slušnosť voči ostatným, ktorí zdieľajú to isté pásmo.

- **LoRa je pomalá technológia.** Dátové rýchlosti sa pohybujú rádovo v stovkách bitov až jednotkách kbps. Je navrhnutá pre krátke, riedke správy — nie pre prenos veľkých dát, hlasu či médií.
- **Zdieľané médium a kolízie.** Všetky uzly na danej frekvencii zdieľajú ten istý kanál. LoRa nemá robustný mechanizmus na riešenie kolízií, takže s pribúdajúcou prevádzkou rastie riziko, že sa pakety navzájom prerušia a reálna priepustnosť klesá.
- **Duty cycle limity.** V EÚ (pásmo 868/869 MHz) platia regulačné obmedzenia — zariadenie smie vysielať len malé percento času. To priamo zastropuje, koľko dát môže uzol odoslať.
- **Half-duplex prevádzka.** Uzly nedokážu súčasne vysielať a prijímať. Kým uzol vysiela, je „hluchý“ voči prichádzajúcim správam. Komunikácia tak musí prebiehať striedavo, čo ďalej znižuje efektívnu priepustnosť a zvyšuje riziko zmeškaných paketov.

Zhrnuté: **vysielací čas (airtime) je vzácny a zdieľaný zdroj.** Každá správa, ktorú odošlete, zaberá čas na pásme aj kapacitu repeatrov v celom regióne. Nasledujúce odporúčania pomáhajú, aby ho sieť využívala čo najlepšie.

### Odporúčané postupy (Do)

- **Nastavte región regionálnym kanálom.** Naša sieť siaha cez Rakúsko, Maďarsko a Slovensko a občas dosiahne aj do Poľska, Rumunska či Slovinska. Keď nastavíte regionálnemu kanálu správny región, hovoríte sieti, kde je správa relevantná a ktoré repeatre ju majú opakovať. Ak píšete do kanála `#bratislava`, nastavte región `sk-ba` — vaša správa sa potom zbytočne neopakuje v Maďarsku a Rakúsku. Pri ostatných regionálnych kanáloch (napr. `#kosice`) zvoľte príslušný región (`sk-ke`), aby správa neblúdila cez pol strednej Európy. Postup nájdete v [zozname kanálov](https://mesh.om3kff.sk/channels.html) a v návode [Ako pridať a nastaviť región](https://mesh.om3kff.sk/channels.html#ako-prida%C5%A5-a-nastavi%C5%A5-regi%C3%B3n). (V odbornej terminológii sa nastavovanie regiónov nazýva *scopovanie*.)
- **Na hľadanie okolitých uzlov použite správny nástroj.** Ak chcete zistiť, ktoré repeatre vás v okolí počujú, použite v klientovi *Tools → Discover nearby nodes*. Je to presne na to určené a nezaťažuje to celý mesh. Posielanie „ping“ do `#ping` alebo „test“ do `#test` namiesto toho zaťažuje celý mesh — takéto správy sa musia re-broadcastnúť cez celú sieť, hoci nikomu nič neprinášajú.
- **Premyslite si bota pred nasadením.** Programovanie je zábava — ak však plánujete bota, zvážte jeho globálnu užitočnosť a nasadenie skonzultujte s komunitou. Spoločne nájdeme spôsob, ako prínos vyvážiť so záťažou, ktorú automatizácia kladie na sieť.

### Čomu sa radšej vyhnúť (Don’t)

- **Časté flood adverty.** Adverty sú zo svojej podstaty flood-scoped — šíria sa celou sieťou a všetky repeatre ich musia re-broadcastnúť. Limitujte flood adverty na nutné minimum (odporúčame raz za ~47 hodín, čo je aj odporúčané [nastavenie repeatra](https://mesh.om3kff.sk/repeater.html#odpor%C3%BA%C4%8Dan%C3%A9-nastavenia) a default v MeshCore 1.16.0).
- **Request-response boti.** Vyhnite sa botom typu otázka-odpoveď (rôzny ping-boti a podobne). Vytvárajú automatizovanú záťaž, ktorá často nezodpovedá ich prínosu pre komunitu.
- **Ne-scopované testovacie správy.** Odolajte pokušeniu posielať testovacie správy bez nastaveného regiónu do testovacích kanálov. Musia sa re-broadcastnúť cez celý mesh a zaberajú drahocenný čas aj pásmo v oblastiach, kde nie sú relevantné.

Vďaka, že beriete tieto odporúčania do úvahy — práve takto zostane sieť rýchla, spoľahlivá a príjemná pre všetkých. 🛜
