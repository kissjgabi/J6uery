## Bevezetés és alapok  

### Kialakulás és használat

<p style="text-align:justify;">A jQuery egy népszerű JavaScript library, mely a HTML kód, és a kliensoldali JavaScript közötti kapcsolatot hangsúlyozza. A jQuery egy erőteljes és népszerű JavaScript keretrendszer, amit John Resig alkotott meg és mutatta be, elsőként a 2006-os New York-i Barcamp-en. A framework a HTML-t és a JavaScript-et igyekszik közelebbi kapcsolatba hozni. Igyekszik a JavaScript-ben megismert technikákat használhatóbbá és egyszerűbbé tenni úgy, hogy az eredeti nyelv erejéből semmit nem veszít. Úgy is írhatunk jQuery kódot, ha nem ismerjük a JavaScript-et, azonban ahhoz hogy a megfelelő eredményeket érjük el fontos, hogy kellően ismerjük az alapot, amire a keretrendszer épül. Filozófiája, hogy amennyire csak lehetséges leválassza a JavaScript kódot a HTML-ből, és különböző eseményvezérlőkön, és azonosítókon keresztül kommunikáljon a weblap HTML elemeivel. A jQuery könnyebbé teszi a javascript használatát:</p>

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
      <script src="jquery.js"></script>
      <script>
          
          <!-- JAVASCRIPT CODE --> 
          
      </script>
  </body>
  </html>
```
### A Dokumentum Objektum Modell (DOM)

<p style="text-align:justify">A DOM egy standard objektummodell, amire a HTML, XML is épül. A modell egymással gyerek-szülő kapcsolatban álló objektumok rendszere. A kialakulása a böngészőháború kezdetére tehető, fejlődése a böngészők, illetve a JavaScript fejlődésével köthető össze. A DOM segítségével érhetjük el a HTML dokumentumunk elemeit, valamint a böngésző eseményeit, mint a kattintás, vagy a görgetés. A DOM-ban az elemeket node-nak, vagyis csomópontnak nevezzük.</p>

#### Alap DOM szerkezet bemutatása:

```html
    <div>
        <p>Szöveg</p>
        <p>Szöveg</p>
    </div>
```

<p style="text-align:justify">A DOM egyes csomópontjaira egykönnyen tudunk hivatkozni illetve bejárni azokat jQuery segítségével.</p>

<p style="text-align:justify">A JavaScript kódot, vagy a linket a külső fájlhoz két helyre tudjuk beszúrni a HTML fájlunkban: a head részbe és a záró body tag elé. Az utóbbinak a teljesítmény szempontjából van jelentősége, hiszen a kód a HTML kód után töltődik le.
    
Ezzel elő is jön az első probléma a JavaScript kódok futtatása során. Ha a JavaScript/jQuery kód a head részben található, akkor a kód az előtt fut le, mielőtt létre jönne maga a HTML dokumentum és annak a DOM-ja, vagyis mivel a kód lefutásakor még nem létezik, így módosítani/hozzáférni sem tudunk. Erre jelenthet megoldást a már említett záró body tag előtti elhelyezés, vagy a JavaScript-ben használatos onload eljárás jQuery megfelelője a ready() eljárás.</p>

```js
    $(document).ready(function() {
        console.log( "Ready!" );
    });
```

<p style="text-align:justify">A fenti kódrészlet belsejében található console.log() függvény akkor fut le, ha a dokumentum teljesen betöltött. A kijelelőben található document elnevezéssel a dokumentumot jelöljük ki, míg a ready() eljárás segítségével elérhetjük, hogy a kód az oldal letöltődése után fusson le, vagyis akkor amikor már kész a HTML szerkezet.

Ugyanennek a megoldásnak létezik egy rövidebb változata, melyben a $ (jQuery definiáló karakter) után egy üres függvényt nyitunk, amiben elhelyezzük a futtatni kívánt kódot. Az üres függvény hívás egy megszokott eljárás jQuery-ben, amivel még sokat találkozunk az egyéb eljárások visszatérése során.</p>

```js
    $(function() {
        $("div").click(function() {
            $("body").css("background", "#ccc");
        });
    });
```

<p style="text-align:justify">A fent bemutatott kódrészlet, miután a dokumentum betöltött, kattinthatóvá teszi a div elemünket. Az a kattintás hatására az egész törzs hátterét #ccc értékűre állítja.

Próbáljuk ki a jQuery mindkét féle beágyazási módját a következő példán:</p>

```html
<!doctype html>
<html lang="hu">
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no" />

    <title>Demo</title>
      
    <script src="jquery.js"></script>
    <script>
        $(document).ready(function() {
            $("*").click(function() {
                $("span#jquery").css("color", "blue");
          });
        });
    </script>
  </head>
  <body>
      <span id=jquery>JQuery</span> <span class=demo>demo</span>
      <script>
          $("#jquery").hover(function() {
            $(".demo").css("font-style", "italic");
          });
      </script>
  </body>
  </html>
```
| [View sample01](bevezetes01demo.html) |
| :----: |

<p style="text-align:justify">A fejrészben megadott jQuery kódban – ahol kötelezően meg kellett adnunk a dokumentum betöltésére vonatkozó eseményt – a weblap akármelyik részére történő klikkelés esetén a span típusú jquery azonosítójú HTML tag betűszíne kékre vált. Míg a törzs végén specifikált kódban, ha jquery azonosítójú elem fölé visszük az egeret, akkor a demo osztályú szöveg dőlt betűstílusúvá válik (itt nem szükséges a dokumentum betöltődésére megszorítást tennünk).

Készítsünk egy olyan oldalt, amin megjelenik egy link, és rákattintásra egy figyelmeztető ablak ugorjon fel.</p>

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
      <script src="jquery.js"></script>
      <script>
        $(document).ready(function() {
            $("a").click(function( event ) {
                alert( "The link is broken!" );
                event.preventDefault();
            });
        });
      </script>
  </body>
  </html>
```
| [View sample02](bevezetes02demo.html) |
| :----: |

<p style="text-align:justify">A 15. sor megakadályozza az alapértelmezett viselkedést, vagyis a link ne töltődjön be, hanem egy figyelmeztető ablak bukkanjon fel.

A jQuery egy lenyűgöző eszköz, segít abban, hogy hogy hatékonyabbak legyünk. Az elsajátítása egy kis előismeret után meglepően gyorsan véghez vihető. Azonban fontos, hogy tisztában legyünk a HTML/CSS, JavaScript, DOM alapjaival. Természetesen előnye és hátránya is van a keretrendszerek használatának. Mivel nagy mennyiségű kódrészletet tesz közénk és a programnyelv közé figyelnünk kell rá, hogy a lehető leghatékonyabb kódot írjuk meg, hogy a programjaink kellően gyorsak legyenek. Ez ugyan hátrány, de jobb kód írására ösztönöz minket. Előny, hogy a böngészők kompatibilitásával nem kell foglalkoznunk, megoldja a jQuery.</p>

