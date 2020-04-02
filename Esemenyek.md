## Események

<p style="text-align:justify">Az események talán a legérdekesebb összetevői a JavaScript-nek, így érthető, hogy nagyon nagy figyelmet kapott a jQuery tervezőitől is. Az eseményekkel dinamikus, vagyis a felhasználói interakcióra reagáló oldalakat hozhatunk létre. Ha például, a felhasználó kattint az egérrel, vagy leüt egy billentyűt, a programunk képes érzékelni ezt és reagálni rá.</p>  

### Események bemutatása

<p style="text-align:justify">Egy eseményt gyakran használtunk az eddigiek során is. Mindig ezt a kódot hívtuk meg, ha akkor akartuk elindítani a kódunkat, amikor a DOM már betöltött.</p>

```js
    $(function() {
        // kód
});
```

<p style="text-align:justify">Az egyik leggyakoribb esemény a click(), ami akkor hívódik meg, amikor a felhasználó egy megadott elemre kattint. A kód megváltoztatja a div méretét 200px-re, ha rákattintunk a div-re. A használata a következő:</p>  

```js
    $(function() {
        $("div").click(function() {
            $(this).width("200px");
        });
    });
```

<p style="text-align:justify">Rengeteg esemény kezelő eljárás létezik a jQuery-ben, ez fel is vetett egy problémát, túl komplikálttá tette a sok esemény az egyszerű használatot. Természetesen a logikájuk hasonlóan egyszerű, mint az eddig tanultak, azonban rengeteg van belőlük.</p>  

<p style="text-align:justify">Az 1.7-es verzióval változott a helyzet. Megjelent két új esemény kezelő eljárás, az on() és az off(). Ennek a két eseménykezelőnek az a célja, hogy összefogja az összes, az eseményekért felelős eljárást és egy kalap alá vegye.</p>  

<p style="text-align:justify">A hivatalos dokumentum, események böngészése során, szinte mindenhol azzal találkozunk, hogy a különálló események használata helyett, az 1.7-es verzió óta az on() esemény kezelő eljárás használata az ajánlott. Mivel első sorban ma már ez a támogatott, így az a legcélszerűbb, ha mi is ezt használjuk.</p>  

<p style="text-align:justify">Nézzük, hogy a fenti kattintásos példánk, hogy néz ki on() esemény kezelő megvalósítással.</p>  

```js
    $(function() {
        $("div").on("click", (function() {
            $(this).width("200px");
        });
    });
```

<p style="text-align:justify">Láthatjuk, hogy a különbség nem nagy. Ezentúl, ha egy esemény kezelőt szeretnénk használni, tudni fogjuk, hogy az on() eljárást kell meghívnunk és ebben elhelyezni, az esemény nevét. Az összes létező eseményt használhatjuk az on()-on belül!</p>  

### Trigger() eljárás

<p style="text-align:justify">A trigger() eljárás segítségével manuálisan előidézhetünk egy eseményt. Ez elsőre kicsit zavarosnak tűnhet, de nézzük meg működés közben. Tehát, az eddigi kódunkban, kattintanunk kellett ahhoz, hogy megnöveljük a div elemünk méretét 200px-re, azonban ha bővítjük a kódunkat:</p>  

```js
    $(function() {
        var div = $("div");
        
        div.on("click", (function() {
            $(this).width("200px");
        });

        setTimeout((function() {
            div.trigger("click");
        }, 2000);
    });
```

<p style="text-align:justify">Ebben az esetben, miután frissítjük az oldalt, a div 2 másodperc után 200px szélesre vált, vagyis előidéztünk egy kattintás eseményt, a trigger eljárás segítségével.</p>  

<p style="text-align:justify">Felmerül a kérdés, milyen gyakorlati haszna lehet ennek a dolognak? A későbbi tanulmányaink során bőven találkozhatunk a trigger() eljárással, azonban most nézzünk egy esetet, amikor egy tetszőleges link elemhez rendelünk egy submit eseményt egy űrlapon belül.</p>  

```html
    <form method="GET">
        <a>Űrlap küldése</a>
    </form>
```

```js
    $(function() {
        $("a").on("click", (function() {
            $("form").trigger("submit");
        });
    });
```

<p style="text-align:justify">Az űrlapot GET eljárással küldjük el. Az a elemhez hozzárendelünk egy click() eljárást, visszatérési értékeként pedig megadjuk, hogy küldje el a trigger() eljárás segítségével az űrlapot.</p>  

### Hozzáadott események feloldása

<p style="text-align:justify">Az események létrehozását angolul binding-nak nevezzük, ami lényegében kötést jelent. Az események feloldását, pedig unbinding-nak. Számos eset előfordulhat, amikor felakarunk oldani egy eseményt, teszem azt, szeretnénk ha egy gombot csak x-szer lehet lenyomni. Ebben lesz segítségünk az on() eljárás párja, az off().</p>  

<p style="text-align:justify">Az előző példából, most kikapcsoljuk az űrlap elküldésért felelős click() eseményt. A kód bővítése után, az űrlapot nem tudjuk elküldeni.</p> 

```js
    $(function() {
        $("a").off("click");
    });
```

### Esemény objektum

<p style="text-align:justify">Az esemény objektum egy, a visszatérési függvény hívás során megadható objektum, ami számos dolgot megmutat nekünk az aktuális eseményünkről.</p>  

```js
    $(function() {
        var div = $("div");
        
        div.on("click", (function(event) {
            console.log(event);
        });
    }); 
```

<p style="text-align:justify">Futtatva a fenti kódrészletet megkapjuk az eseményünk objektumát, amiben hatalmas adatmennyiséget találunk, amiket esetlegesen fel használhatunk. Például megtudhatjuk az egér kattintási pozícióját:</p>  

```js
    $(function() {
        var div = $("div");
        
        div.on("click", (function(event) {
           alert(
                 "x koordinata: " + event.pageX +
                 "y koordinata: " + event.pageY 
           );
        });
    }); 
```

### Esemény átruházás

<p style="text-align:justify">Az Event Delegation egy nagyon hasznos része a jQuery fejlesztési menetének. A legjobb fordítás talán az esemény átruházás. A delegation az események felhalmozódásának a problémáját oldja meg. Előfordulhat, hogy egy oldalon több 10, vagy akár több 100 elemünk van, amihez hozzárendeltünk egy eseményt. Ez a dolog elsőre sem hangzik jól. Van 50 elemünk és mindegyikhez ugyan az az esemény tartozik, 50 különböző esemény, amiket a jQuery egy ciklus segítségével megy végig.</p>  

<p style="text-align:justify">A delegation lényegében úgy működik, hogy nem közvetlenül az elemekhez rendeljük az eseményt, hanem a szülő elemhez, amiben megtalálhatóak az elemek. Így elérjük, hogy csak egy eseményt hozunk létre, ami az aktuális eseményt megvizsgálja és alkalmazza a gyerek elemeken. Az esemény átruházást szintén az on() eljárás segítségével tudjuk alkalmazni.</p>  

```html
    <ul>
        <li>Bekezdés 01</li>
        <li>Bekezdés 02</li>
        <li>Bekezdés 03</li>
        <li>Bekezdés 04</li>
        <li>Bekezdés 05</li>
        <li>Bekezdés 06</li>
        <li>Bekezdés 07</li>
        <li>Bekezdés 08</li>
        <li>Bekezdés 09</li>
        <li>Bekezdés 10</li>
    </ul>
```

```js
    $(function() {
        $("ul").on("click", "li", (function() {
            alert("Esemény átruházás");
        });
    });
```

<p style="text-align:justify">Az esemény átruházás áthidal még egy problémát. Ha dinamikusan jQuery-vel hozunk létre egy elemet, akkor kódból a módosításaink már nem érvényesek rá. Tehát ha a fenti eseményeket simán, delegáció nélkül rendelnénk az elemekhez és hozzáadnánk egy új elemet, akkor az új elemen nem működne az esemény, mivel egy időben jöttek létre. A delegációs megoldás, viszont egy elem gyerek elemeit nézi, így miután létrehoztuk az új elemet, újra megnézi azok számát.</p>  

### Esemény terjedés

<p style="text-align:justify">Az Esemény Terjedés, vagyis az Event Propagation szintén egy alapvető jQuery problémára kínál megoldást. Mégpedig a gyerek szülő elemekben található események külön futtatására.</p>  

```html
    <p><span>Propagation</span> Egy normális bekezdés </p>
```

```js
    $(function() {
        $("span").on("click", (function() {
            alert("Span elem kattintás!");
        });
        $("p").on("click", (function() {
            alert("P elem kattintás!");
        });
    });
```

<p style="text-align:justify">Az elmélet a következő: ha egy ős – leszármazott kapcsolat során, mind az ős és mind a leszármazott kap egy eseményt, akkor a gyerek esemény megörökli az ős elem eseményét.</p>  

<p style="text-align:justify">A megoldásban a már megismert esemény objektum lesz a segítségünkre, ami nem csak adatokat, de függvényeket is tartalmaz. A leszármazott eseményt meghívjuk, az event objektummal és használjuk a stopPropagation() függvényt, ami megállítja, hogy lefusson az ős eseménye.</p>  

```js
    $(function() {
        $("span").on("click", (function(event) {
            alert("Span elem kattintás!");
            event.stopPropagation();    
        });
        $("p").on("click", (function() {
            alert("P elem kattintás!");
        });
    });
```

<p style="text-align:justify">Az esemény a JavaScript lelke. Hatalmas dinamikát adhatunk a segítségével az oldalunknak. A jQuery-ben tovább fejlesztették őket és jóval könnyebben kezelhetőek.</p>  
