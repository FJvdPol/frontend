# Codenotes

# You don't know JS - Types & Grammar
## 1. Types
Een *type* definieert een verschil in *value* binnen javascript.

### Alle types:
* `number`
* `string`
* `boolean`
* `object`
* `null`
* `undefined`
* `symbol` -- ES6

```js
typeof undefined     === "undefined"; // true
typeof true          === "boolean";   // true
typeof 42            === "number";    // true
typeof "42"          === "string";    // true
typeof { life: 42 }  === "object";    // true

// added in ES6!
typeof Symbol()      === "symbol";    // true
```

Let op! null is buggy
```js
typeof null === "object" // true
```

test voor exact null door deze methode:
```js
var waarde = null;
(!waarde && typeof waarde === "object"); // true
```

en functions?
```js
typeof function functie(a, b){} === "function" // true
```

Functions zijn subtypes van objects, dus kunnen properties hebben.
```js
// volgens functie declaratie hierboven
functie.length; // 2 (a en b)
```

en arrays?
```js
typeof [1, 2, 3] === "object" // true

```
subtype van object

Undefined is niet hetzelfde als undeclared!
```js
var a;
console.log (a); // undefined
console.log(b); // refError: b is not defined
```
maar de types van a en b in dit geval zijn hetzelfde:
```js
typeof a; // Undefined
typeof b; // Undefined
```

## 2. Values
### Arrays
Arrays zijn variables waarin meerdere values opgeslagen zijn.
Voorbeelden van values in arrays kunnen zijn:
* Numbers
* Strings
* Andere arrays
* Objects
* Variables
etc.

```js
var a = [ ];
a[0] = 1
a[1] = "Hallo"
a[2] = [1, 2, 3]
a.length // 3
console.log(a[2]) // [1, 2, 3]
console.log(a[4]) // undefined

// Pas op met het overslaan van indexes! Lengte kijkt naar begin tot eind index.
a[5] = 3;
a.length; // 6, terwijl a[4] nog steeds undefined is omdat we daar niets in hebben gestopt.
```

Aangezien een array een subtype is van object kunnen er ook properties in zitten. Deze tellen niet mee met de length property.
```js
var a = [ ] ;
a[0] = 2;
a["hallo"] = 3;

a.length; // 1

a["hallo"]; // 3
a.hallo; // 3
```
Maar wanneer de stringname geinterpreteerd kan worden als getal telt het wel mee:
```js
var a = [ ] ;
a[0] = 3;
a["12"] = 3;
a.length; // 13
```
TL;DR gebruik geen strings als array indexes. Als je een waarde wil koppelen aan een woordindex, gebruik objects:
```js
var a = [];
var o = {};
a[0] = 1;
o.groet = "Hallo";
```

#### Array-likes
het veranderen van een nodelist in een echte array (met alle methods die er op toegepast kunnen worden):
```js
var elements = document.querySelectorAll('div'); // is soort array van elementen, maar kan geen gebruik maken van de array methods indexOf(), concat() etc.
var arr = Array.prototype.slice.call( elements ); // nu kan ie dat wel want we veranderen de nodelist in een echte array.
```

### Strings
Hoewel strings veel methods delen met arrays, zoals .length, .concat() etc. Zijn ze niet hetzelfde.
```js
var a = ["f", "o", "o"];
var b = "foo"
a.length; // 3
b.length; // 3
a[1] = "x";
b[1] = "x";
console.log(a) // ["f", "x", "o"]
console.log(b) // "foo"
```
Strings zijn meer *immutable* dan arrays.

Oftewel, een gedeelte van een array aanpassen overschrijft makkelijk, maar een string aanpassen vergt het creeëren van een hele nieuwe string.
```js
var a = "foo"
a.toUpperCase(); // "FOO"
a; // "foo" --> de waarde van a is hetzelfde gebleven.

var c = a.toUpperCase();
a === c // false
a; // "foo"
c; // "FOO"
```
TL;DR: we kunnen geen methods van arrays gebruiken op strings, wanneer deze de *originele waarde aan zouden passen*.
Alle andere methods zijn beschikbaar, zoals .length

### Numbers
Nummers in javascript kunnen zowel integer als decimal zijn. Alleen is een integer niet echt een integer (heel getal) maar kan ook een heel getal met 0 als decimal zijn.
```js
var a = 1 // integer
var a = 1.0 // integer
var a = 1. // integer (is hetzelfde als 1.0)
var a = 1.11 // decimal
var a = 0.11 // decimal
var a = .11 // decimal (zelfde als 0.11)
```

Je kunt hele kleine of grote getallen opschrijven in exponent form
```js
var a = 5E10;
a; // 50000000000
a.toExpontential(); // "5e+10"
```

je kunt variables met een number value gebruik laten maken van de methods van het Number object.
```js
var a = 42.59;
a.toFixed(0); // "43"
a.toFixed(1); // "42.6"
```
let op , de output komt als string terug

## 3. Natives
Object wrapper:
```js
var s = new String("abc");
var d = "abc";
s; // String {0: "abc"}
d; // "abc"
typeof s; // Object
typeof d; // String
```
Dus, var s heeft alle methods van het object prototype én het String prototype object. Var d heeft alleen de methods van het String prototype object.

## 4. Coercion
## 5. Grammar
