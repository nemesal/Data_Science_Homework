# Gázos Mese

Spreadmonitória királysága kicsi, mindenestől elfér a Ménesi úton, viszont a lakók annyira imádják a
gázt, hogy még a napokat is gáznapban számolják: egy-egy gáznap magyar idő szerint reggel 6-tól
másnap reggel 6-ig tart. A királyságba egyetlen csövön (ún. átadón) érkezik a gáz, amely három
fogyasztót (ún. POD, point of delivery) lát el: a kocsmát, az elnöki palotát és a picligyárat.
Mindhárom helyen okosmérőket szereltek fel, amelyek óránként küldögzetik a mért gázfogyasztás-
értékeket egy adatbázisba. A királyságban okos emberek élnek, akik már régóta mentegetik a helyben
tapasztalt és előrejelzett hőmérséklet-értékeket ugyanebbe az adatbázisba.

Nem véletlenül, ugyanis a hatóságoknak mindig előre meg kell tippelni, mennyi gáz fogy majd a
királyságban. Mindezt rögtön kétféleképpen:

- Az ún. nominálás azt jelenti, hogy gáznaponként összegezve mondjuk meg, szerintünk mennyi gáz fogy
  majd a gáznap alatt az átadón. Ezt értelemszerűen ugyanabban a mértékegységben mérjük, mint amiben
  az óránkénti gázfogyasztás van: kWh-ban. A hatóság akkor büntet, ha az általunk nominált gáznapi
  érték pluszmínusz 14%-os környezetéből kikerül a tényleges gázfogyasztás, a büntetés ekkor arányos
  a nominált és a tényleges kWh-érték különbségének abszolút értékével.

- Az ún. kapacitás-lekötés azt jelenti, hogy gáznaponként mondjuk meg, mennyi lesz az átadón mért
  maximális órás fogyasztás. Ezt kWh/h-ban mérjük: ha pl. egy gáznap alatt az átadón a nap első 8
  óráján át 10 kWh fogy minden órában, majd a maradék 16 órán át 15 kWh fogy óránként, akkor a
  tényleges kapacitás 15 kWh/h lesz. A kapacitás-lekötésnek díja van: minden lekötött kWh/h-ért
  c forintot kell fizetni. Hatósági bünti csak akkor van, ha a tényleges kapacitás túllépi az előre
  lekötött (és díjban kifizetett) mennyiséget, a bünti mértéke minden túllépett kWh/h-ért 4c forint.

2020 október 24., szombat hajnal van, éppen reggel hat óra. Mindhárom pod éppen beküldte a friss
fogyasztási adatát, miközben az éjjeli bulitól kábán nézed a képernyőt. Azonnal be kell küldened a
nominálást és a kapacitás-lekötést a hétvégére! A hatóságok tehát 4 számot várnak tőled: nominálást
illetve kapacitás-lekötést, a szombati és vasárnapi gáznapokra. Minden szám az átadóra érvényes, a 3
fogyasztási hely együttesére.

A hatóságokon kívül mi még várjuk tőled a kódot, ami az előrejelzést produkálta, esetleg akár
részeredményeket is az oda vezető úton, és mindenképpen valamilyen adatvizualizációt, ami meggyőzi a
hatóságokat - és minket.

## Adatok

Három adatfájlt találsz mellékelve.

A `consumption_history.csv` a három fogyasztási hely (`pod`) múltbeli fogyasztott kWh-értékei
(`kwh`) óránként (`time`). Minden időpont-oszlop mindhárom fájlban UTC-ben van, és az adott egyórás
intevallum elejét jelenti (tehát pl. `2018-11-06 05:00:00+00:00` a UTC-beli 5-től 6-ig, Budapesten
6-től 7-ig tartó intervallumot jelenti, mivel ekkor 1 óra az eltolódás, éppen a gáznap első órája).

A `temperature_history.csv` a historikus hőmérséklet-értékek (`temp`) Celsiusban, óránként (`time`).

A `temperature_forecast.csv` a hőmérsékleti előrejelzéseket tartalmazza ugyanígy Celsiusban,
óránként. Ez a fájl - a másik kettővel ellentétben - nyers adatbázis adatokat tartalmaz, így meg
kell tisztítani: az adott órára elérhető legfrissebb előrejelzést kell venni. Az oszlopok jelentése:

- `id` - sorazonosító.

- `created_at` - sor keletkezésének időbélyegzője

- `updated_at` - sor módosításának időbélyegzője

- `row_version` - ennyiszer volt a sor módosítva

- `date_time` - ezzel az időponttal kezdődő egy órára vonatkozik a hőmérséklet

- `resolution` - `PT60M`, egyórás felbontás

- `temperature` - hőmérséklet Celsiusban

- `source` - `D` mint Dark Sky, a sor forrása

- `estimated` - `TRUE`, ebben a fájlban csak becsült értékek vannak.

- `location__id` - `1`, melyik helyszínre vonatkozik a hőmérséklet, ezúttal a Clark Ádám térre.

## Adminisztráció

Bármilyen programnyelvben neki lehet ugrani, de ha a megoldás nem Pythonban van, nem feltétlenül 
tudjuk majd lefuttatni magunk, így akkor részletesebb részeredményeket kérünk. A megvalósítást 
teljesen rád bízzuk, Jupyter Notebook is teljesen jó, ami a részeredményekkel dokumentálja
ömnagát.

A feladattal fél napnál többet ne tölts és a project root-ban egy README.md-ben foglald össze, hogy
mivel kb. mennyi időt töltöttél, mivel akadtál el stb. (elég néhány mondatban). Ha esetleg nem 
végzel mindennel fél nap alatt az nem gond, akkor a részeredményt küldd be nekünk.

Ha bárhonnan nagyobb kódrészletet másolsz, akkor jelöld meg, hogy ki az eredeti tulaj és igyekezz 
ezt kerülni (nem az egyszerűbb stack overflow thread-re gondolunk). Pythonnál kizárólag open-source 
package-eket használj.

A kész munkát küldd el zippelve egy emailben, vagy ha szeretnéd, töltsd fel a GitHubra és hívd meg 
collaborator-ként [nyooc](https://github.com/nyooc) felhasználót. Ha bármi kérdés felmerül, keresd
bátran Balázst a <balazs.varga@spreadmonitor.com> címen! Hajrá!
