## Pre používateĺov

Vďaka OM2AMT máme rozbehnutú testovaciu prevádzku bridge SK ⇄ CZ, momentálne na kanáli `#cs`.

### Ako to funguje teraz

Momentálne stále čakáme na nasadenie `cs` regiónu najmä na českých repeatroch, preto sa odporúča ho nepoužívať v cezhraničnej komunikácii.
Ak budete písat na kanál `#cs` nenastavujte, prosím, žiadny región.

### Ako to bude fungovať neskôr

Keď bude mať región `cs` nastavených vačšina repeatrov:

1. V klientovi nastavíte **Predvolený región** na `cs`.
2. Pošlite **flood advert**. Dorazí až do Česka.
3. Keď to isté urobí váš partner v Česku, môžete si písať súkromné správy, akoby ste boli v jednej sieti.

## Pre Operátorov repeatrov
### Pridanie regiónu `cs`

Okrem kanálov by sme chceli povoliť aj súkromné správy a ďalšiu komunikáciu. To bude možné až vtedy, keď bude mať región `cs` pridaný väčšina repeatrov na Slovensku aj v Česku. V Bratislave je už pridaný na väčšine repeatrov.

**Pridajte na svoje repeatre región `cs`.**

<img src="img/App_Scopes_cs.png" alt="Nastavenie regiónov" style="max-width: 100%; height: 250px"/>

Možte tiež použiť príkazový riadok:
```
region put cs
region save
```
