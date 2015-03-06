class: title
background-image: url(images/tarkovsky3.jpg)

.titles[
# Treasures from<br>React.js Conf 2015

.author[
  Paul Wittmann &mdash; [@wakkahari](https://twitter.com/wakkahari) &mdash; <paul@railslove.com>
]]

???
+ Entwickler bei **Railslove**
+ **28./29.** Januar in SF
+ erzählen warum React gerade solche **Wellen** schlägt; **Ideen** vorstellen, **Neugier** wecken
+ **kein Tutorial**, kein "React im Vergleich zu Angular/Ember/..."

---

class: background-cover where-we-stand
background-image: url(images/Ricoh-GR-sample-images-3.jpg)

# Where we stand

???
### Stand von **User Interfaces** mit JavaScript
+ User Interfaces sind schwer: frameworks **sprießen aus dem Boden**
+ HTML wasn't built for web apps
+ ob React bleibt wird die Zeit sagen
+ lange nicht mehr so begeistert von neuen Ideen
+ andere Frameworks bauen gerade fleißig React nach

---

class: what-is-react
background-image: url(images/rat_tribe_zhang_hai_hai.jpg)

.overlay[
# What is React?
]

???
Ok, was is überhaupt React?

---

class: muffin
background-image: url(images/muffin-with-bits-funky.png)

???
+ **Struktur** meines Vortrags ist: wenn React ein Muffin wäre...
+ **Smartie-Stückchen**: Schätze / Killer Features
+ **Farben** stehen für Konzepte und Ideen, die diese Features möglich machen

(Teig: glue code ;p)

---

class: muffin
background-image: url(images/muffin.png)

???
+ **Umriss**

---

class: colour-stripes

.stripe.stripe--green[]
.stripe.stripe--blue[]

???
+ Auffrischerkurs in **Farblehre**
+ **Ideen** hinter React
+ Kern den ich **vermitteln** will

---

class: muffin
background-image: url(images/muffin-only-green-and-blue.png)

???
+ ein paar Schokostückchen der React Conf rauspicken

# -> zunächst aber zum Umriss

---

class: vertical-center vertical-center-large

.vertical-title[
  outline
]

JavaScript _library_ for<br> building **user interfaces**

???
+ Mitte 2013, Facebook
+ skeptische Reaktionen - selbst erst durch Om überzeugt.

<br>
+ **Erwartungshaltung**: kein **Framework**
+ the "V" in MVC - kein MVC, aber mehr als nur "V", da andere Ideen
+ **Virtual DOM** -> great performance; und das war's - es geht um mehr.

<br>
+ flexibles Werkzeug, schränkt mich nicht ein wie ein Framework ("A product with the business logic removed, but all of the assumptions left in." (Devil’s Dictionary of Programming))
+ lässt sich leicht in bestehende Lösungen **integrieren**

---

class: vertical-center vertical-center-left

.vertical-title[outline]

+ don't learn a **framework's language**
+ **flexible tool** to model business logic in the language of the problem domain

---

class: vertical-center vertical-center-large

.vertical-title[alien technology]

makes us think and<br>
**challenges** us

???
+ React ist uns erstmal **fremd** - Alien Technology; JSX, templates und view in gleicher Datei
+ Wir sind immer noch dabei zu entdecken was dank React alles möglich ist.
+ Input und **Erweiterungen** der **Clojure community**.
# -> nun zur Farblehre

---

class: vertical-center vertical-center-medium vertical-center-left

.vertical-title[ideas]

.green[easy to **reason about**]
<br>
<br>
.blue[don't care about **rendering**]

???
**zwei zentrale Aspekte** von React anschauen
**nachvollziehen** was der Code macht
**jQuery Spaghetti**: alles feuert auf den DOM

---

class: vertical-center vertical-center-medium vertical-center-left

.vertical-title[architectural concepts]

.wrapper[
.green[
.small[easy to reason about]
**separation** of concerns]
<br>
.blue[
.small[don't care about rendering]
DOM is **abstracted away**]
]

???
rendering: rerender everything, virtual DOM as an implementation detail to make this possible

---

class: vertical-center vertical-center-medium vertical-center-left

.vertical-title[implementation]

.wrapper[
.green[
.small[easy to reason about > separation of concerns]
**components**]
<br>
.blue[
.small[don't care about rendering > DOM is abstracted away]
**Virtual DOM**]
]

???
rendering: rerender everything, virtual DOM as an implementation detail to make this possible

---

class: code-fullscreen component-example

```html
<script src='react.js'></script>
<script src='JSXTransformer.js'></script>

<div id='example'></div>

<script type='text/jsx'>
  var ButtonCounter = React.createClass({
    getInitialState: function() {
      return { count: 0 };
    },

    addOne: function() {
      this.setState({ count: this.state.count + 1 });
    },

    render: function() {
      return <div>
          <div>{ this.state.count }</div>
          <button onClick={ this.addOne }> +1 </button>
        </div>
    }
  });

React.render(<ButtonCounter />,
             document.getElementById('example'));
```

???
+ **Atomare Einheit** einer React-Anwendung

---

class: vertical-center vertical-center-large

.vertical-title[Pete Hunt]

data changing over time is the **root of all evil**

???
+ schwierig nachzuvollziehen - erst recht wenn es mehrere Beteiligte gibt
+ state einer Facebook **Kontaktliste** nach Änderungen
# -> in React gibt es deshalb...

---

class: vertical-center vertical-center-large

_state_ -vs- _props_

---

class: code-fullscreen component-example

```html
<script src='react.js'></script>
<script src='JSXTransformer.js'></script>

<div id='example'></div>

<script type='text/jsx'>
  var ButtonCounter = React.createClass({
    getInitialState: function() {
      return { count: 0 };
    },

    addOne: function() {
      this.setState({ count: this.state.count + 1 });
    },

    render: function() {
      return <div>
          <div>{ this.state.count }</div>
          <button onClick={ this.addOne }> +1 </button>
        </div>
    }
  });

React.render(<ButtonCounter />,
             document.getElementById('example'));
```

---

# Props

.large-code[
```html
<FriendListItem>
  <FriendListInfo name="Darth Vader"
    mutual_friends_count=100 />
</FriendListItem>
```
]

---

class: vertical-center vertical-center-large

_state_ -vs- _props_

???
### Unterscheidung
+ **state** ist veränderbar, aber wir nur von dieser Komponente verändert
+ **props** sind unveränderbar
+ macht Code viel besser nachvollziehbar wenn ich weiß dass etwas nicht verändert werden kann

---

class: background-stretch-vertical mutable-state-is-bad
background-image: url(images/davis-mutable-state-is-bad.png)

---

class: vertical-center vertical-center-large

unidirectional data flow

???
immer von Parent zu Child.

---

class: vertical-center vertical-center-large

.vertical-title[when data needs to travel upstream]
Flux

???
+ child -> parent (z.b. Toggler) oder inputs
+ kein **Flux** heute, aber dafür ein verwandtes Problem

---
class: vertical-center vertical-center-large

How do components get the **data** they need?

---

class: vertical-center vertical-center-large

.vertical-title[alien territory ahead]

**GraphQL** and **Relay**

???
+ **GraphQL**: Abfragesprache, die Relay möglich macht, hat nix mit der GraphAPI zu tun
+ **Relay**: Integration dieser Sprache mit React

---

background-image: url(images/components-example.png)

???
**Composable**: ich kann Components ineinander schachteln

---

background-image: url(images/relay-01.png)

---

background-image: url(images/relay-02.png)

---

background-image: url(images/relay-03.png)

---

background-image: url(images/relay-04.png)

---

background-image: url(images/relay-05.png)

---

background-image: url(images/relay-06.png)

---

class: vertical-center vertical-center-large background-blue

Rendering

---

background-image: url(images/davis-prismatic-example-01-before-cropped.png)

---

background-image: url(images/davis-prismatic-example-02-after-cropped.png)

---


class: vertical-center vertical-center-large background-blue

.vertical-title[rendering]
f: data -> UI

???
+ seitdem wir **jQuery Spaghettiland** hinter uns gelassen haben modellieren wir UI-Logik mit **JS Daten** (DOM nicht mehr als Datenspeicher)

---

class: background-black

background-image: url(images/doom3-react.png)

---

jQuery: imperatives Spaghettifest mit dem DOM
Backbone: Templates, aber imperativer Code, der granulare nachträgliche Änderungen vornimmt
React: deklarativ, render-Funktion beschreibt wie die UI zu allen Zeiten auszusehen hat - was sie dank ständigem Neurendern auch tut.

---

JavaScript data -> DOM

prismatic example from Ian Davis

---

Problems:

+ how to keep everything in synch?
+ how to keep things performant?
  -> precise DOM updates

---
class: vertical-center rerender-everything

when you call `setState`,  
_everything_ gets rerendered

---
class: vertical-center vertical-center-large

How can that ever work?

---

React completely abstracts away the DOM

???
"we never interact with the DOM itself, we just interact with React components and they propagate all the necessary changes for us" (Ian Davis)

---

data -> render function -> virtual DOM elements

---

class: code-fullscreen component-example

```html
<script src='react.js'></script>
<script src='JSXTransformer.js'></script>

<div id='example'></div>

<script type='text/jsx'>
  var ButtonCounter = React.createClass({
    getInitialState: function() {
      return { count: 0 };
    },

    addOne: function() {
      this.setState({ count: this.state.count + 1 });
    },

    render: function() {
      return <div>
          <div>{ this.state.count }</div>
          <button onClick={ this.addOne }> +1 </button>
        </div>
    }
  });

React.render(<ButtonCounter />,
             document.getElementById('example'));
```

---

class: vertical-center
React is all about components

???
no models, no controllers, templates are part of the components, in the future CSS will live there as well.
"Rethinking best prectices."

---

JSX

???
use the power of JavaScript - no need for a DSL templating language
quite the opposite of logicless templating :)

className: b/c that's what it's called in the DOM specification - https://developer.mozilla.org/en-US/docs/Web/API/Element/className
htmlFor: same reason, https://developer.mozilla.org/en/docs/Web/API/HTMLLabelElement

---

Rendering
- Performance
- server-side rendering via node (Angular haben's aufgegeben)
- Einfachheit - ich muss weniger nachdenken wenn immer alles neu gerendert wird - weniger DOM state - keinen den ich manage
- früher: es gab klickpfade bei denen bestimmte sachen kaputt gingen - extrem schwer zu verwaltender view state - lese eine nachricht, eine neue kommt rein, dann klicke ich auf xxx und dann geht auf einmal yyy nicht mehr.

- nutzen JS wo's nur geht - [].map, inline styles etc.
- schneller einstieg, leicht granular einzubauen - kein riesen setup. schnell erste ergebnisse, fühlt sich gut an.

früher: jQuery - wieviele elemente der klasse .foo gibt es um zu wissen wieviele fotos im galerieslider sind
dann backbone - wie update ich nur den namen im DOM wenn ich nur ein event habe, dass der user sich geändert hat?

Template: so wie in vielen anderen JS Frameworks auch.
Problem: früher haben wir den DOM als Datenspeicher missbraucht - Datenattribute, Galleriekarussell bei dem wir den DOM mit `$('.galleryImage').length` abfragen wieviele Bilder gerade da sind.
Dann kam Backbone - Models als "single source of truth".
Problem weiterhin: wenn sich ein Teil des Models ändert wird alles komplett neu gerendert das auf Änderungen des Models hört
-> viel Code geschrieben um das zu umgehen / performanter zu machen.
Computer können das besser, wir sollten uns wegen sowas nicht den Kopf zerbrechen müssen - wird sehr schnell chaotisch und unbeherrschbar.

einfachste Lösung:
- bei Änderung am Model alles neu rendern, um alle Stellen im DOM zu aktualisieren
- ähnlich wie wenn Seiten auf dem Server gerendert werden
- bisher nicht sehr performant, ABER:
... virtueller DOM (nicht Shadow DOM)

muss mir als entwickler keine gedanken darum machen.

auch in react: ein model an mehrere views binden spannt viele stricke -> stores in flux / globalere date (Om)

JSX template mit state

präzisere updates
ich muss mich nicht drum kümmern

React:
- Rendering und Datenstrukturen sind Implementierungsdetails
  saubere, flexible Plattform auf die es aufzubauen lohnt
- geht mehr darum die Ideen zu vermitteln - wenn ihr alle morgen anfangt React zu nutzen bin ich sehr froh, aber wenn ihr immutable.js oder [virtual-dom](https://github.com/Matt-Esch/virtual-dom) in euren Projekten einsetzt bin ich auch froh :)

---

# React Native

???
Virtual DOM - doesn't matter where you're actually rendering - can easily be exchanged

---

The biggest benefit of React Native isn't JavaScript. It’s React.

[http://red-badger.com/blog/2015/03/04/react-native-the-killer-feature-that-nobody-talks-about](http://red-badger.com/blog/2015/03/04/react-native-the-killer-feature-that-nobody-talks-about)

---

# GraphQL & Relay

---

class: background-cover contents
background-image: url(images/Ricoh-GR-sample-images-3.jpg)

# Contents
0\. What is React?  
1. Demos  
2. Big Announcements  
3. Beyond React  

???

+ Demos: Ryan Florence's "Hype!" Vortrag
+ 2 große Ankündigungen: 1. React Native und 2. Relay & GraphQL
+ Beyond: Immutable.js, Om

---

???
+ JavaScript Bibliothek von Facebook um User Interfaces zu bauen.
+ steckt in: Facebook, Instagram, Atom Editor, Flipboard, Airbnb, Atlassian Hipchat
+ kein MVC, "das _V_ in MVC"
+ funktional geprägt
+ inpsiriert von Rich Hickeys Einfachheitsbegriff (cf. [Simplicity matters](https://www.youtube.com/watch?v=rI8tNMsozo0))

---

class: vertical-center
JavaScript _library_ for building UIs

---

component with JSX example

render method calls functions, embraces JS and its data structures - doesn't need models ("React quickly became known as the 'V' in MVC and people kept asking what do I use for the 'M' then? The answer is you don't need an 'M', you have JavaScript arrays and objects already.")

---

# React Summary

+ components
+ virtual DOM
+ simplicity

???
Einfachheit:
+ JS nutzen wo's nur geht - keine Turing-vollständige Templatingsprache, JSX ist eine dünne Schichte über reinen JS-Funktionen, JS um CSS zu schreiben.
+ JS Datenstrukturen für Models nutzen
+ Performanz ist nur eine Folge der Einfachheit, kein Ziel - man kann alles schnell kriegen und es gibt Lösungen die schneller als React sind.
+ mentalen Tribut gering halten, einfach über Code nachdenken, Bugs schnell fixbar machen

---

class: vertical-center

React Native

???
native apps with React

---

# More treasures

+ David Nolen, Cognitect: ["React Refracted"](https://www.youtube.com/watch?v=5hGHdETNteE)
+ Lee Byron, Facebook: ["Immutable Data and React"](https://www.youtube.com/watch?v=I7IdS-PbEgI)

???
Dome of the cathedral of Florence

---

class: vertical-center vertical-center-large

.wrapper-center[
Summary
<br>
.railslove-heart[![heart](images/railslove-heart.svg)]
]

---

class: vertical-center

.wrapper[
# React Europe
2-3 July, Paris

[react-europe.org](http://www.react-europe.org)
]

---

.vertical-center.large[
Questions
]

---

# Links
+ [React.js Conf 2015 Videos](https://www.youtube.com/playlist?list=PLb0IAmt7-GS1cbw4qonlQztYV1TAW0sCr)
+ [The Future of JavaScript MVC Frameworks](https://swannodette.github.io/2013/12/17/the-future-of-javascript-mvcs)
+ [Removing User Interface Complexity, or Why React is Awesome](http://jlongster.com/Removing-User-Interface-Complexity,-or-Why-React-is-Awesome)
+ [React’s diff algorithm](http://calendar.perfplanet.com/2013/diff)
+ [Coming to React from Angular](http://www.stridenyc.com/blog/2015/3/4/coming-to-react-from-angular)
+ [Hotloader](https://www.youtube.com/watch?v=pw4fKkyPPg8)

+ [React & Om](https://paulwittmann.github.io/cgnjs-om)
+ [My Way into Clojure: Building a Card Game with Om](http://www.railslove.com/stories/my-way-into-clojure-building-a-card-game-with-om-part-1)
