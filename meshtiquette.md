### Ako sieť funguje a prečo na tom záleží

MeshCore je mesh sieť postavená na LoRa rádiách, kde uzly (nodes) preposielajú správy cez viacero skokov (multi-hop) a tým rozširujú dosah bez potreby infraštruktúry. Aby sieť dlhodobo dobre fungovala, je dobré rozumieť jej prirodzeným limitom — a podľa toho sa správať. Nejde o pravidlá, ale o slušnosť voči ostatným, ktorí zdieľajú to isté pásmo.

- **LoRa je pomalá technológia.** Dátové rýchlosti sa pohybujú rádovo v stovkách bitov až jednotkách kbps. Je navrhnutá pre krátke, riedke správy — nie pre prenos veľkých dát, hlasu či médií.
- **Zdieľané médium a kolízie.** Všetky uzly na danej frekvencii zdieľajú ten istý kanál. LoRa nemá robustný mechanizmus na riešenie kolízií, takže s pribúdajúcou prevádzkou rastie riziko, že sa pakety navzájom prerušia a reálna priepustnosť klesá.
- **Duty cycle limity.** V EÚ (pásmo 868/869 MHz) platia regulačné obmedzenia — zariadenie smie vysielať len malé percento času. To priamo zastropuje, koľko dát môže uzol odoslať.
- **Half-duplex prevádzka.** Uzly nedokážu súčasne vysielať a prijímať. Kým uzol vysiela, je „hluchý“ voči prichádzajúcim správam. Komunikácia tak musí prebiehať striedavo, čo ďalej znižuje efektívnu priepustnosť a zvyšuje riziko zmeškaných paketov.

Zhrnuté: **vysielací čas (airtime) je vzácny a zdieľaný zdroj.** Každá správa, ktorú odošlete, zaberá čas na pásme aj kapacitu repeatrov v celom regióne. Nasledujúce odporúčania pomáhajú, aby ho sieť využívala čo najlepšie.

### Odporúčané postupy (Do)

- **Scopujte svoju prevádzku.** Naša sieť siaha cez Rakúsko, Maďarsko a Slovensko a občas dosiahne aj do Poľska, Rumunska či Slovinska. Scope je „flag“, ktorý hovorí, kde je správa relevantná a ktoré repeatre ju majú opakovať. Ak píšete do kanála `#slovakia`, použite scope `sk` — vaša správa sa potom zbytočne neopakuje v Maďarsku a Rakúsku. Pri regionálnych kanáloch (napr. `#kosice`) zvoľte užší scope ako `sk-ke`, aby správa neblúdila cez pol strednej Európy.
- **Na hľadanie okolitých uzlov použite správny nástroj.** Ak chcete zistiť, ktoré repeatre vás v okolí počujú, použite v klientovi *Tools → Discover nearby nodes*. Je to presne na to určené a nezaťažuje to celý mesh.
- **Premyslite si bota pred nasadením.** Programovanie je zábava — ak však plánujete bota, zvážte jeho globálnu užitočnosť a nasadenie skonzultujte s komunitou. Spoločne nájdeme spôsob, ako prínos vyvážiť so záťažou, ktorú automatizácia kladie na sieť.
- **Think before you type.** Nezáväzný pokec patrí ku komunite — pred odoslaním správy len krátko zvážte, akú pridanú hodnotu prináša.

### Čomu sa radšej vyhnúť (Don’t)

- **Časté flood adverty.** Adverty sú zo svojej podstaty flood-scoped — šíria sa celou sieťou a všetky repeatre ich musia re-broadcastnúť. Limitujte flood adverty na nutné minimum (odporúčame raz za ~48 hodín).
- **Request-response boti.** Vyhnite sa botom typu otázka-odpoveď (rôzne ping-boti a podobne). Vytvárajú automatizovanú záťaž, ktorá často nezodpovedá ich prínosu pre komunitu.
- **Ne-scopované testovacie správy.** Odolajte pokušeniu posielať testovacie správy bez scope do testovacích kanálov. Musia sa re-broadcastnúť cez celý mesh a zaberajú drahocenný čas aj pásmo v oblastiach, kde nie sú relevantné.

Vďaka, že beriete tieto odporúčania do úvahy — práve takto zostane sieť rýchla, spoľahlivá a príjemná pre všetkých. 🛜
