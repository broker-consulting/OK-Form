## Dokumentace k projektu

Zdravím všechny, kdo si to budou číst, tady je stručný popis zadání, cílů, plánů, výhod a nevýhod kódu, na kterém jsem pracoval.

Zadal mi to taťka, kerý chtěl SW nástroj, kde budou moct interně hlasovat členové investičního výboru. Kompletní mail je níže, ale TL;DR: První krok (tento kód) je zlepšit podobu hlasování a používat vlastní statickou webovou stránku místo Google Form.

Pracoval jsem na tom sám s LLMkama, protože po doptání na bezpečnost mi bylo řečeno, že hlasování není tajné, a já jsem odprezentoval myšlenku, že pro frontend je AI více než dostatečná a případné chyby v kódu jsou estetické, ne bezpečnostní.

Původní koncept byl, že uživatelé vyplnili ok-form, jednoduchý alg. to převedl do CSV a ten odeslali kolegům na mail. Ti ho pak měli překopírovat do Excelu manuálně.
To se jim nepozdávalo, tak jsem přidal celou komplexitu pro GitHub Actions: máme `ok.form.monecois@gmail.com` účet, který sbírá odpovědi z formuláře a GitHub Actions je zpracovává a ukládá do CSV. To je pak možné stáhnout z repozitáře a otevřít v Excelu.

Je to na můj vkus "alternativní" / až moc kreativní řešení. Ale cíl byl vyhnout se AI generovaným databázím a backendu + vejít se do nevelkého časového/finančního okna. (Nastala klasická situace, kdy očekávání komplexity SW převažovalo všechny kapacity...)
Ale je to fáze 1, kde jen zkoušíme, jestli s tím budou všichni OK a na pořádnou full-stack aplikaci budu potřebovat aspoň jednoho kolegu/kolegyni, abychom to udělali zabezpečeně a kvalitně.


### Origo mail:
```
Ahoj kluci,
posílám propojovaci email kontaktu.

Chtěli bychom naši hlasovací proceduru investičního výboru převést do  interní web aplikace a opustit V první fázi Google form a v druhé fázi opustit XLS

Michaeli, Vojto, Peťo, prosím můžete se potkat a ukázat si jak to dnes funguje a jak to udělat? Péťa by nám naprogramoval tu apku

Kdybyste chtěli něco upřesnit, Ondra nebo já jsme k dispozici

Ohledně cloudoveho úložiště prosím na Erika

Fakticky to vidím na 3 oddělene kroky

1) replikovat Google hlasovací formulář ale vylepšit kontrolu hlasování podle daných pravidel, což Google form neumí.

Agregovat hlasovací lístky jednotlivců a Exportovat csv tohoto hlasování pro další ruční zpracování v existujících Excelech

2) opustit excel a mít to vše v aplikaci, včetně historie hlasování. Prostor pro nějaký Dashboard, ukazující nejen aktuální pozici ale i historii a vývoj hladovani jednotlivců i skupin

3) Mít schopnost vyhodnotit hlasovani proti indexům a dělat atribuční analýzu kde se nám daří a kde nedaří apod = mít na měsíční frekvenci historii výkonnosti reprezentativních indexů tříd aktiv a témat o kterých se hlasuje atd

V této fázi prosím jen bod 1)
Mobily pošlu přes SMS samostatně

Dekuju moc!
Petr
```


### Současné problémy, které potřebuji s Vámi vyřešit
<ul>
  <li> složka data/kola obsahuje historii halsování v public repozitáři. Zatím jsem hlasoval jen já, tudíž to nevadí a v private repu jsem to nepovažoval za problém. Data jsou ale zatím i v Excelu (ke kroku 2 jsme se ještě nedostali), takže můžu dopsat kód pro vymazání historie po dokončení hlasování.
  <li> Celý koncept byl vytvořen pro GitHub během léta. Převod na GitLab jsem zatím nedělal, ale věřím, že to s CI/CD nebude problém (jen jsem čekal na vaše rozhraní, abychom to rovnou zapojili).
  <li> Nemám z fin-tech procesami zatím zkušenost, tak budu čekat na verdikt, ale mám zkušenosti s full-stack vývojem a těším se na spolupráci.
  <li> Ano, frontend je vibe coded (ale vědomě). A "backend" a "databáze" jsou manuálně nastavené obchůzky, které jsou momentálně nakonfigurované pro GitHub. (Obojí rozhodnutí bylo konzultováno a prezentováno i s popsanými riziky a sám si za volbou pro tuto fázi stojím :) )
  <li> Účet `ok.form.monecois@gmail.com` může být dočasný, nebo ho mohu předat komukoliv dalšímu.
</ul>
