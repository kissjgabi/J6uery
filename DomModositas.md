## DOM modosítás

<p style="text-align:justify">Eddigi tanulmányaink alapján mostanra már bármilyen elemet kitudunk jelölni a DOM szerkezetekben. Ezzel feljebb léptünk egy fokkal és haladhatunk tovább a következő nagyobb egység felé. Ez az egység a DOM módosítás, amit a kijelölések megtanulása után egész egyszerűen tudunk majd végrehajtani.</p>  

### Elem értékének kinyerése és beállítása – text(), html()

<p style="text-align:justify">A text() és a html() eljárás két testvér eljárás, azzal a különbséggel, hogy a html() eljárással HTML elemeket is hozzáadhatunk egy elemhez, míg a text()-el nem. Ha a text() eljárás során html elemeket adunk meg, akkor a program a <> jeleket átalakítja entitásokká, így elérve, hogy a böngésző megjelenítse ezeket a karaktereket, ne pedig értelmezze.</p>  

Példával szemléltetve a dolog a következőképpen néz ki:

```html
    <p>Bekezdés 1</p>
    <p>Bekezdés 2</p>
```

```js
    $(function() {
        var p = $("p");
        
        p.first().text("text() eljárás ");
        p.first().html("html() eljárás ");
    });
 ```

Ez a két eljárás felül írja az elemek addigi tartalmat!

Két verziót különböztetünk meg mind a kettőből:

+ $(“p”).text(); – Vissza adja az adott elem tartalmát, amit tetszőlegesen eltárolhatunk.  

+ $(“p”).text(“Bekezdés!”); – Beállítja az adott elem tartalmát.  

+ $(“p”).html(); – Vissza adja az adott elem tartalmát, amit tetszőlegesen eltárolhatunk.  

+ $(“p”).html(“Bekezdés!”); – Beállítja az adott elem tartalmát.

<p style="text-align:justify">A html() eljárást használhatjuk kisebb feladatoknál, azonban komplikáltabb HTML elemek létrehozására létezik egy jobb megoldás!</p>  

### Elem hozzáadása – wrap(), prepend(), append(), before(), after()

<p style="text-align:justify">Háromféle elem hozzáadási kategóriát tudunk megkülönböztetni aszerint, hogy hova kerül a beillesztett elem a meglévőhöz képest.</p>  

#### Hozzáadás az elem köré

##### wrap(), wrapAll(), wrapInner()

Az alábbi kód segítségével az első p elemet becsomagoltuk egy div elembe.

```js
    $(function() {
        var p = $("p");
        
        p.first().wrap("</pre>");
    });
```

<p style="text-align:justify">A wrapAll() eljárással több elemet csomagolhatunk be egyszerre. Jelen esetben két bekezdésünk van, így a wrapAll()-al elérhetjük, hogy mind a két elemet becsomagoljuk egy div elemmel.</p>  

```js
    $(function() {
        var p = $("p");
        
        p.first().wrapAll("</pre>");
    });
```

<p style="text-align:justify">A wrapInner() eljárás segítségével egy adott elem tartalmát csomagolhatjuk be egy elembe. Tehát, ha az első p elemünk köré wrapInner()-el hozzáadunk egy strong elemet, akkor a strong elem a p elemen belül jelenik majd meg.</p>

```js
     $(function() {
        var p = $("p");
        
        p.first().wrapInner("<strong />");
    });
```

<p style="text-align:justify">Az elemek hozzáadása során használhatunk rövidítést a fent bemutatott módon, így nem kell mindig leírnunk a nyitó és záró tag-eket, elég csak egy, saját magát lezáró elem.</p>

#### Hozzáadás elemen belül

##### append() appendTo() prepend() prependTo() text() html()

<p style="text-align:justify">A text() és a html() eljárásokat már ismerjük, így ezekkel bővebben már nem foglalkozunk.</p>

<p style="text-align:justify">Az append() és a prepend() testvér eljárások. Mind a kettő az előzőleg megadott elemet helyezi el a kijelölt elemen belül. A különbség az, hogy az append() az elemben lévő elemek mögé helyezi el az új elemet, míg a prepend() az elemek elé.</p>  

```js
     $(function() {
        var p = $("p");
        
        p.first().append("<span>append</span>");
        p.first().prepend("<span>prepend</span>");
    });
```

<p style="text-align:justify">Az appendTo() és prependTo() ugyan azt a feladatot látja el, mint a append() és a prepend(), csak másfajta megközelítést használ. Ebben az esetben a hozzáadni kívánt elem a kijelölő helyén helyezkedik el, a kijelölő pedig a függvény értékeként.</p>

```js
     $(function() {
        var p = $("p");
        
        $("<span>append</span>").appendTo(p);
        $("<span>append</span>").prependTo(p);
    });
```

#### Hozzáadás elemen kívül

##### after() before() insertAfter() insertBefore()

<p style="text-align:justify">Az elemen kívüli hozzáadás eljárások az elemen belüliek ellentéte, vagyis a kijelölt elem elő vagy mögé helyezik el a megadott elemet.</p>

<p style="text-align:justify">Az after(), before() eljárás értelemszerűen az elem elé és mögé helyezi el az új elemet. A létrehozott két új bekezdés a megadott bekezdéssel egy szinten kerül beszúrásra, az elem elé és mögé.</p>

```js
     $(function() {
        var p = $("p");
        
        p.last().before("<p>before</p>");
        p.last().after("<p>after</p>");
    });
```

<p style="text-align:justify">Az insertBefore() és insertAfter() az appendTo és a prependTo logikájával egyenértékűek, vagyis elsőként kell megadnunk a beszúrni kívánt elemet, míg másodikként az eljáráson belül a kijelölőt.</p>

### Elem eltávolítása – remove(), empty()  

<p style="text-align:justify">A remove() eljárás segítségével nem csak elemeket távolíthatunk el a DOM-ből hanem eljárásokat is. Használata a fent említett módosító függvényekéhez hasonló. Kijelöljük az elemeket, majd hozzáfűzzük a remove() eljárást. A remove() eljárást tovább szűrhetjük. Ha csak az olyan p elemeket akarjuk kiszűrni, amiknek van egy class tulajdonsága, akkor a függvényen belül meg kell adnunk ezt a kijelölőt.</p>  

```js
      $(function() {
        var p = $("p");
        
        p.remove();
        p.remove(".first");
    }); 
```

<p style="text-align:justify">Az empty() eljárás segítségével kiüríthetjük a kijelölt elemet, tehát kitörölhetjük a gyerek elemeit. Természetesen ettől a kijelölt elem megmarad, viszont az összes tartalma eltűnik.</p>

```js
      $(function() {
        var p = $("p");
        
        p.first().empty();
    });  
```

### CSS tulajdonság módosítása – css()

<p style="text-align:justify">A css() eljárás egy erőteljes és jól használható eszköz. A text() és html() eljáráshoz hasonlóan ez is képes csak érték visszaadásra, ha az eljáráson belül csak a CSS tulajdonság nevét adjuk meg akkor annak értékét kapjuk vissza. Figyelnünk kell arra, hogy az itt használt tulajdonságok megadása során nem használhatunk a CSS-ben megszokott rövidítést, mint a margin, helyette mindig a pontos meghatározást kell megadnunk, mint a margin-right/margin-left.</p>

```js
      $(function() {
        var bg = $("p").css("background");
        
        alert(bg);
    });  
```

Az eljárás használatának a megszokott módja a név – értékpárok alkalmazása:  

```js
      $(function() {
        var p = $("p");
        
        p.last().css("background", "aqua");
    });  
```

<p style="text-align:justify"><Jól látható, hogy így több tulajdonságot nem tudunk megadni egyszerre. Szerencsére erre is létezik megoldás./p>

```js
       $(function() {
        var p = $("p");
        
        p.first().css({
            "background" : "aqua"),
            "padding-left" : "50px"
            });
    });  
```

<p style="text-align:justify">Nagy mennyiségű használat során ez a megoldás nem a legkifinomultabb. Ha sokat használunk ehhez hasonló kódokat, akkor érdemes megfontolnunk a osztály kijelölő módosító eljárások használatát. Így előre megírhatjuk egy elem formázását CSS-ben és egy addig nem létező osztályhoz rendelhetjük őket. Ezt az osztályt később jQuery segítségével hozzáadjuk.</p>

+ addClass() – Hozzáad egy, vagy több elemet a kijelölt elemhez.  

+ removeClass() – Eltávolít egy, vagy több elemet a kijelölt elemhez.  

+ toggleClass() – Váltogat a hozzáadás és eltávolítás között attól függően, hogy létezik, vagy sem az adott érték.

```js
      $(function() {
        var p = $("p");
        
        p.last().addClass("test");
        p.last().removeClass("test");
        p.last().toggleClass("test");
    });  
```

### Új elemek létrehozása  

<p style="text-align:justify">A fent taglalt függvényekkel hozzáadás során megadhatjuk a zárójelek között a hozzáadni kívánt elemeket és azok tulajdonságai, azonban sok esetben ez körülményes. Van egy jobb és átláthatóbb megoldás is!</p>

```js
      $(function() {
        var p = $("p").last();
        
        var newDiv = $("<div />", {
            "text" : "Elem hozzáadása komplex elem létrehozásával",
            "class" : "box"
        }).appendTo(p);
    });  
```

<p style="text-align:justify">Ezzel a módszerrel objektumszerűen hozhatunk létre új elemeket. Első lépésben az elem típusát adjuk meg, majd ezután a tulajdonságait.</p>

<p style="text-align:justify">A DOM módosítások megértésével már kézzel fogható jQuery tudásunk van, hiszen már komoly változtatásokat tudunk végrehajtani a dokumentumunkban.</p>
