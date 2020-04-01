## DOM bejárás

<p style="text-align:justify">A DOM bejárás ( angolul traversing ) egy fontos része a JavaScript/jQuery-nek. A jQuery DOM bejárás segítségével bejárhatjuk a dokumentumunk szerkezetét és megkereshetjük azt az elemet/elemeket, amire éppen szükségünk van. Mindezt úgy tehetjük meg, hogy figyelembe vesszük az elhelyezkedését a többi eleméhez képest. Addig ugrálunk a különböző szinteken, amíg el nem érünk ahhoz, ami nekünk kell.</p>

<p style="text-align:justify">Lényegében 5 fajta relációt különböztetünk meg a kapcsolódó elemek között. A gyerek – szülőt, leszármazott – ős/felmenőt és a testvért. Ezek tulajdonképpen mind a való életből vett kapcsolatok. A gyerek – szülő egyértelmű, azonban ebben az esetben egy gyereknek, csak egy szülő elme lehet, viszont egy szülőelemnek számtalan gyerek eleme. A leszármazott – felmenő, hasonlítható a nagyszülőkre, dédszülőkre. Ha egy elemnek kijelöljük a felmenőit, akkor visszakapjuk az összes létező felmenőjét, ugyan ez igaz, ha kijelöljük a leszármazottait, mindet visszakapjuk. A testvér elem kijelölővel a dokumentumban az egy szinten lévő elemeket jelölhetjük ki.</p>

<p style="text-align:justify">Mint tudjuk a DOM egy olyan strukturált szerkezet, ahol az elemek alá és fölé rendeltségi viszonnyal kapcsolódnak egymáshoz. A DOM bejárása tulajdonképpen a kijelölési módszerek finomítása. Nézzük példával illusztrálva.</p>

Adott az alábbi DOM szerkezet:

```html
    <div>
        <p>Bekezdés 1</p>
        <p class=""text>Bekezdés 2<strong>Leszármazott </strong></p>
        <p>Bekezdés 3</p>
        <p>Bekezdés 3</p>
    </div>
```

<p style="text-align:justify">Jól látható, hogy szerkezetileg a p elemek a div elem gyerekei, vagyis a div elem a p elemek szülő eleme. Tudjuk azt is, hogy a p elemek egymás testvérei, mivel egy szinten helyezkednek el. Tovább megfigyelhetjük azt is, hogy a strong elem a div elem leszármazottja, valamint a div elem a strong elem ős eleme. Ez a tudás valószínű ismerős a HTML/CSS ismereteink megszerzése során. Nézzünk pár kijelölést!</p>

Elsőként jelöljük ki a második p elemet:

```js
 
 
 ```

<p style="text-align:justify"></p>

```js
 
 
 ```

<p style="text-align:justify"></p>

```js
 
 
 ```

<p style="text-align:justify"></p>

```js
 
 
 ```

<p style="text-align:justify"></p>
