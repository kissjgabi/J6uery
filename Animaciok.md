## Animációk  

 <p style="text-align:justify">A jQuery animáció funkcióinak köszönhetően látványos mozgásokat, áttűnéseket hozhatunk létre pár sor kóddal. Nyugodtan kijelenthetjük, hogy nagy részben az animate() eljárásnak és társainak köszönhetően szerzett ekkora felhasználói tábort a keretrendszer.</p>  
 
 <p style="text-align:justify">A fő eljárás az animációk készítése során az animate(). Az eljárás és egy két CSS tulajdonság – érték pár segítségével számos dolgot animálhatunk. A gyakrabban használatos animációs módokhoz létrehoztak külön eljárásokat, mint a fadeIn()/fadeOut() vagy a slideIn()/slideOut().</p>  
 
### Alapszintű animáció – show(), hide(), toggle()
 
 <p style="text-align:justify">A show() és a hide() eljárás magukért beszélnek, megjelenítik, illetve elrejtik a kívánt elemet.</p>  
 
```js
     $(function() {
        var p = $("p");
        
        p.hide();
        p.show();
     });
```
 
 <p style="text-align:justify">Ebben a formában, csak elrejtik az elemet, bármiféle animáció nélkül, azonban a függvénynek van egy idő paramétere, ahol megadhatjuk ezredmásodpercben az animáció lezajlásának idejét, természetesen a már sokszor használt callback függvényt itt is használhatjuk!</p>  
 
```js
     $(function() {
        var p = $("p");
        
        p.hide(2000);
        p.show(2000);
     });
```
  
 <p style="text-align:justify">A harmadik említett eljárás a toggle(). A toggle tuljadonképpen egy kepcsoló, jelen esetben, ha az adott elem látszik, akkor elrejti, ha nem látszik akkor megjeleníti. A következő esetben a p elemek megjelennek:</p>  
 <p style="text-align:justify">Sorkizárt szöveg.</p>  
 
```js
     $(function() {
        var p = $("p");
        
        p.hide(2000);
        p.toggle(2000);
     });
```
 
 ### Átfedés animáció – fadeIn(), fadeOut(), fadeToggle(), fadeTo()  
 
 <p style="text-align:justify">A fadeIn() és a fadeOut() eljárás testvérpáros, hiszen az egyik a megjelenésért, míg a másik az eltűnésért felelős, egyébként ugyanúgy működnek. A fadeToggle() a fent taglalt szimpla toggle() eljrásához hasonlóan egy kapcsoló a látható és az elrejtett állapot között. Mind a három függvény a visszatérési érték mellett egy lefutási idő paraméterrel rendelkezik.</p>  
 
```js
     $(function() {
        var div = $("div");
        
        div.fadeOut(2000);
        div.fadeIn(2000);
        div.fadeToggle(2000);
        div.fadeToggle(2000);
     });
```
 
 <p style="text-align:justify">A fadeTo() eljárás használatához plusz egy paraméter szükséges, ami az átfedés mérete, 0-1-ig kell megadnunk azt az értéket, amennyi átfedést szeretnénk. Tehát a függvény nem teljesen elrejt, vagy megjelenít, csak egy bizonyos százalékig teszi.</p>  
 
```js
     $(function() {
        var div = $("div");
        
        div.fadeTo("2000", 0.4);
     });
```

### Csúszó animáció – slideDown(), slideUp(), slideToggle()

<p style="text-align:justify">A slideDown() eljárás legördíti, vagyis megjeleníti az adott elemet, míg a slideUp() felgörgeti, vagyis elrejti. A slideToggle() pedig szintén a két állapot közötti kapcsoló.</p>  
 
```js
     $(function() {
        var div = $("div");
        
        $("button").click(function() {
             div.slideToggle();
        })
     });
```

### Animáció eljárás – animate()

<p style="text-align:justify">Az animate() eljárás használata során a CSS tulajdonságokat kell használnunk. A függvény szintaxisa a következő:</p>  

```js
    .animate( properties [, duration] [, easing] [, complete] );
```
 
<p style="text-align:justify">Tehát az eljárás használatához 4 paramétert hívhatunk segítségül. Az első a tulajdonságok, amit objektumszerűen adhatunk meg, a második a hossz, a harmadik a dinamika, míg a negyedik a visszatérési érték. Egyszerű példával illusztrálva:</p>  

```js
     $(function() {
         $(".klikk-animate").clicl(function() {
             $(".animate").animate({
                  opacity: '0.5',
                  height: '200px',
                  width: '200px'
             }, 2000);
         });
     });
```

<p style="text-align:justify">Ha több fajta dinamika/easing beállítást szeretnénk használni, akkor használnunk kell a jQueryUI-t!</p>  
<p style="text-align:justify">Jól látható, hogy az animáció a CSS tulajdonságokra támaszkodik és azokat módosítja a megadott értékekre. A használható CSS tulajdonságok mindegyike felveheti a “hide”, “show” és “toggle” értéket. Ezekkel megjeleníteni, vagy elrejteni tudjuk a különböző animációkat. A toggle pedig a már megismert, jQuery esemény követő. A szám értékeket adhatunk meg relatívan a “+=” vagy “-=” karaktersorozatokkal, tehát ha egy értéket növelni szeretnénk 50-el, akkor a megadás a következő: left: ‘+=50’.</p>  

### Animáció léptetés

<p style="text-align:justify">A fenti példában egyszerre három tulajdonságot animáltunk, azonban megtehetjük azt is, hogy a tulajdonságokat egymás után módosítjuk. Ezzel a lehetőséggel nagyon sok különböző animáció típust hozhatunk létre. A jQuery intelligensen kezeli az események sorba állítását!</p>  


```js
     $(function() {
         $(".klikk-animate").clicl(function() {
            var div = $(".animate");

            div-animate({height: "400px", opacity: "0.5"}, "slow");
            div-animate({width: "400px", opacity: "1"}, "normal");
            div-animate({height: "100px", opacity: "0.5"}, "slow");
            div-animate({height: "100px", opacity: "1"}, "normal");
         });
     });
```

### A stop() eljárás

<p style="text-align:justify">A stop() eljárást egy animációs probléma hívta életre, még pedig az, amikor az animációt kiváltó eseményt többször hajtjuk végre, gyorsan egymás után és az animáció beragad, vagyis ahányszor végrehajtottuk a kiváltó eseményt, az animáció annyiszor lejátszódik. Ha a stop() eljárást hozzáfűzzük az animációért felelős kódsorhoz, akkor amikor újra kiváltjuk az elindító eseményt az előző, folyamatban lévő eseményt megszakítja és elindítja újból az animációt.</p>  

<p style="text-align:justify">Az animate() eljárás segítségével, olyan látványos megoldásokat hozhatunk létre, amiket korábban csak Flash technikával. Számos kiegészítő, egyszerűsítő eljárást létrehoztak a tervezők – fadeIn(), slideIn() – hogy egyszerűsítsék a munkánkat.</p>  
