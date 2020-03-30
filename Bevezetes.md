## Bevezetés és alapok  

### Kialakulás és használat

<p style="text-align:justify;">A jQuery egy népszerű JavaScript library, mely a HTML kód, és a kliensoldali JavaScript közötti kapcsolatot hangsúlyozza. A jQuery egy erőteljes és népszerű JavaScript keretrendszer, amit John Resig alkotott meg és mutatta be, elsőként a 2006-os New York-i Barcamp-en. A framework a HTML-t és a JavaScript-et igyekszik közelebbi kapcsolatba hozni. Igyekszik a JavaScript-ben megismert technikákat használhatóbbá és egyszerűbbé tenni úgy, hogy az eredeti nyelv erejéből semmit nem veszít. Úgy is írhatunk jQuery kódot, ha nem ismerjük a JavaScript-et, azonban ahhoz hogy a megfelelő eredmények érjük el feltétlenül fontos, hogy kellően ismerjük az alapot, amire a keretrendszer épül. Filozófiája, hogy amennyire csak lehetséges leválassza a JavaScript kódot a HTML-ből, és különböző eseményvezérlőkön, és azonosítókon keresztül kommunikáljon a weblap HTML elemeivel. A jQuery könnyebbé teszi a javascript használatát:</p>

+ Kezelhetünk eseményeket, pl amikor a felhasználó egy gombra kattint, jelenjen meg egy üzenet.  
+ Létre hozhatunk áttűnéseket, mozgásokat és egyéb látványos effekteket  
+ Hozzá adhatunk elemeket css osztályokhoz, vagy kivehetjük őket onnan  
+ Ajax támogatása: az oldal újra töltése nélkül változtathatunk az oldal tartalmán. Pl meghívhatunk php kódon keresztül sql lekérdezéseket  
+ ... és még sok egyéb hasznos, látványos trükköt végezhetünk  
    
<p style="text-align:justify">Ne felejtsük el, hogy a jQuery is javascript, ezért úgy hozzuk létre oldalunkat, hogy ha a javascript ki van kapcsolva a böngészőben, akkor is élvezhető legyen az oldal használata.</p>

### Alapok

#### jQuery beillesztése a HTML oldalba

<p style="text-align:justify">Látogassunk el a jquery.com oldalra, és a download menüpont alatt töltsük le az egyik fájlt. Több letöltési forrás közül is választhatunk. Mindegyik szerveren 2 fájl közül választhatunk:</p>

+ jquery-x.y.z.js  
+ jquery-x.y.z.min.js  

<p style="text-align:justify">Az első verzió egy jól olvasható, szerkeszthető fájl, a második pedig egy módosított verzió, ami arra törekszik, hogy a fájl minél kevesebb karakterből álljon, azaz egy tömörített verzió. Ha nem akarunk bele nyúlni a jquery könyvtárba, válasszuk a másodikat. Éles környezetben is érdemes ezt használni, hiszen amikor a felhasználó meglátogatja az oldalt, ez a fájl minden oldalfrissítésnél letöltődik hozzá. A fájlt nevezzük át jquery.js-re. ezzel a fájlal megegyező könyvtárban hozzuk létre a html fájlunkat:</p>

```html
<!doctype html>
<html lang="hu">
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no" />

    <title>Demo</title>
  </head>
  <body>
      <a src="https://jquery.com">JQuery</a>
      <script src="jquery.js">
          
          <!-- JAVASCRIPT CODE --> 
          
      </script>
  </body>
  </html>
```
<p style="text-align:justify"></p>

<p style="text-align:justify"></p>

<p style="text-align:justify"></p>

<p style="text-align:justify"></p>

<p style="text-align:justify"></p>
