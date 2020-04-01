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
    $(finction() {
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
    $(finction() {
        var p = $("p");
        
        p.first().wrap("</pre>");
    });
 ```

<p style="text-align:justify">A wrapAll() eljárással több elemet csomagolhatunk be egyszerre. Jelen esetben két bekezdésünk van, így a wrapAll()-al elérhetjük, hogy mind a két elemet becsomagoljuk egy div elemmel.</p>  

```js
    $(finction() {
        var p = $("p");
        
        p.first().wrapAll("</pre>");
    });
```

<p style="text-align:justify">A wrapInner() eljárás segítségével egy adott elem tartalmát csomagolhatjuk be egy elembe. Tehát, ha az első p elemünk köré wrapInner()-el hozzáadunk egy strong elemet, akkor a strong elem a p elemen belül jelenik majd meg.</p>

```js
     $(finction() {
        var p = $("p");
        
        p.first().wrapInner("<strong />");
    });
 ```

<p style="text-align:justify">Az elemek hozzáadása során használhatunk rövidítést a fent bemutatott módon, így nem kell mindig leírnunk a nyitó és záró tag-eket, elég csak egy, saját magát lezáró elem.</p>

#### Hozzáadás elemen belül

##### append() appendTo() prepend() prependTo() text() html()

<p style="text-align:justify">A text() és a html() eljárásokat már ismerjük, így ezekkel bővebben már nem foglalkozunk.</p>

<p style="text-align:justify">Az append() és a prepend() testvér eljárások. Mind a kettő az előzőleg megadott elemet helyezi el a kijelölt elemen belül. A különbség az, hogy az append() az elemben lévő elemek mögé helyezi el az új elemet, míg a prepend() az elemek elé.</p>  

```html


```

<p style="text-align:justify"></p>


```js
 
 
 ```

<p style="text-align:justify"></p>

<p style="text-align:justify"></p>


```html


```

<p style="text-align:justify"></p>


```js
 
 
 ```

<p style="text-align:justify"></p>

