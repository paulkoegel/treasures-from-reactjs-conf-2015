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
+ HTML wurde nicht für **Webapps** gebaut
+ React bringt gehörig **frischen Wind** rein; andere Frameworks bauen gerade fleißig React nach

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
+ **Umrisse skizzieren**

---

class: colour-stripes

.stripe.stripe--green[]
.stripe.stripe--blue[]

???
+ Auffrischerkurs in **Farblehre**
+ **Ideen** hinter React
+ Kern den ich **vermitteln** will
+ Ideen werden uns länger beschäftigen, bin froh wenn ihr **virtual-dom** benutzt

---

class: muffin
background-image: url(images/muffin-only-green-and-blue.png)

???
+ zwei Smarties der React Conf rauspicken: Relay und React Native

# -> zunächst aber zum Umriss

---

class: vertical-center vertical-center-large

.vertical-title[
  outline
]

JavaScript _library_ for<br> building **user interfaces**

???
### Geschichte
+ Mitte 2013, Facebook
+ erste Reaktionen skeptisch - selbst erst durch Om & Pete Hunt überzeugt.
+ Facebook, Instagram, Atom editor, Airbnb, Hipchat

<br>
### Library
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

???
da React eine Bibliothek ist...

---

class: vertical-center vertical-center-large

.vertical-title[alien technology]

makes us think and<br>
**challenges** us

???
+ React ist uns erstmal **fremd** - Alien Technology; JSX, templates und view in gleicher Datei
+ Wir sind immer noch dabei zu entdecken was dank React alles möglich ist.
+ Input und **Erweiterungen** der **Clojure community**.
# -> das war der Umriss, nun zur Farblehre

---

class: vertical-center vertical-center-medium vertical-center-left

.vertical-title[ideas]

.green[easy to **reason about**]
<br>
<br>
.blue[don't care about **rendering**]

???
+ **zwei zentrale Aspekte** von React anschauen
+ leicht **nachvollziehen** was der Code macht; bugs schnell fixen; kurze warmup zeit
+ rendering macht Kopfschmerzen, extrem: **jQuery Spaghetti**: alles feuert auf den DOM

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
**Components**: Bausteine von React
**Virtueller DOM**: Abstraktionsschicht zwischen Components und dem DOM, die DOM-Updates managt

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
# -> zurück auf die Ideenebene, Motivation für Components

---

class: vertical-center vertical-center-large background-green

.vertical-title[Pete Hunt]

data changing over time is the **root of all evil**

???
### Motivation für Components
2 Aspekte
1. schwer nachzuvollziehen wenn Daten die **durch mehrere Funktionen** durchgehen.
2. Bsp.: Bugs, die nur bei bestimmten **Klickpfaden** auftreten nachvollziehen (DOM nicht aktualisiert)

---

class: background-stretch-vertical mutable-state-is-bad
background-image: url(images/davis-mutable-state-is-bad.png)

???
+ simpelstes Beispiel
+ -> Problem liegt noch tiefer: veränderliche Datenstrukturen haben (-> **Immutable.js**)
# -> Reacts Lösung:

---

class: vertical-center vertical-center-large background-green

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

???
state kennen wir schon.

# direkt weiter machen

---

class: background-green

# Props

.large-code[
```html
<FriendListInfo name="Darth Vader"
       mutual_friends_count=100 />
```
]

???
von außen gesetzte Attribute

---

class: vertical-center vertical-center-large background-green

_state_ -vs- _props_

???
### Unterscheidung
+ **state** ist veränderbar, aber wird nur von dieser Komponente verändert
+ **props** sind _für diese Komponente_ unveränderbar
+ zähmt das **Mutable State Monster**
+ macht Code viel besser nachvollziehbar wenn ich weiß dass etwas nicht verändert werden kann

---

class: vertical-center vertical-center-large background-green

_unidirectional_ data flow

???
immer von Parent zu Child.

---

class: vertical-center vertical-center-large background-green

.vertical-title[when data needs to travel upstream]
Flux

???
+ child -> parent (z.b. Toggler) oder inputs
+ kein **Flux** heute, was neueres

---

class: vertical-center vertical-center-large background-green

How do components get the **data** they need?

---

class: vertical-center vertical-center-large background-green

.vertical-title[alien territory ahead]

**GraphQL** and **Relay**

???
+ **GraphQL**: Abfragesprache, die Relay möglich macht, hat nix mit der GraphAPI zu tun
+ **Relay**: Integration dieser Sprache mit React

---

background-image: url(images/components-example.png)

???
+ **verschachtelt**
+ **Daten**:
  - Array von Freunden
  - Avatar, Freundschaftsstatus
  - Name, # gemeinsame Freunde

---

background-image: url(images/relay-01.png)

???
auf **Server** muss das gleiche Wissen stecken damit wir nicht zu viele API Requests machen müssen

---

background-image: url(images/relay-02.png)

???
bei Änderungen: überall anpassen :(

---

background-image: url(images/relay-04.png)

???
+ Components und API-Daten dazu

---

background-image: url(images/relay-05.png)

???
lassen wir die Values weg haben wir unsere **Datenanforderungen** :)

---

background-image: url(images/relay-06.png)

???
das ist **GraphQL**
hat **serverseitige** Komponente

---

class: vertical-center vertical-center-large background-green

**Relay**

???
+ GraphQL in React
+ Komponenten spezifizieren ihre Datenanforderungen
+ Eltern verweisen auf die Anforderungen ihrer Kinder
+ Rootkomponente aggregiert alle Anforderungen und schickt GraphQL Anfrage an Server

---

background-image: url(images/relay-example.png)

???

# -> ENDE DER GRÜNEN PERIODE

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
**Components**: Bausteine von React
**Virtueller DOM**: Abstraktionsschicht zwischen Components und dem DOM, die DOM-Updates managt

---

class: vertical-center vertical-center-large background-blue

**Rendering**

???
Blaue Periode

---

background-image: url(images/davis-prismatic-example-01-before-cropped.png)

???
wenn ich Urban Exploration **followe** passiert...

---

background-image: url(images/davis-prismatic-example-02-after-cropped.png)

???
Probleme:
+ **synchron halten** = aufwändig
+ mehrere DOM-Updates oft nicht **performant**

# -> Performance Beispiel

---

background-image: url(images/monkeys-slow.gif)

???
+ textbox mit mathematischen Formeln

---

class: vertical-center vertical-center-large background-blue

.vertical-title[React's solution]

rerender _everything_

???
+ wenn **setState** aufgerufen wird
+ **simpelste Lösung**
+ **nie im Leben performant**

---

class: background-black

background-image: url(images/doom3-react.png)

???
+ schwarz-weiß: Doom 3 Rendering Engine
+ Blau-weiß: React-Entsprechungen
+ VDOM = **JS objekt**
+ **minimale Änderungen** gehen an echten DOM

---

class: vertical-center vertical-center-medium vertical-center background-blue

+ precise DOM updates
+ DOM abstracted away

???
+ erlaubt deklaratives Bauen von UI aus JavaScript Daten
+ React Entwickler modifizieren nicht direkt den DOM.

---

class: vertical-center background-blue

.vertical-title[better performance through simplicity]

"making an entire family of common and tedious **hand optimization** techniques **obsolete**"

???
David Nolen. "The Future of JavaScript MVC Frameworks"

---

class: vertical-center vertical-center-large background-blue

.wrapper[
# React Native

build **native apps** with React
]

???
Virtual DOM - doesn't matter where you're actually rendering - can easily be exchanged

---

class: vertical-center background-blue

.wrapper[
+ JS runtime --**asynchronously**-> native thread
+ "**learn once**, write anywhere"
+ web development experience 
]

???
1. write JS & React, runs on a **JS runtime** renders to **native views**
2. **the platforms are different** - not the same code but the same stack - **the platforms are different**
3. no compilation step

---

class: large-code background-blue

```html
<View>
  <Text numberOfLines={2}>
    {this.props.movie.title}
  </Text>
</View>
```

???
+ instead of **div** and **span**
+ native views are simply **different**
+ write once run anywhere is a **pipe dream**

---

class: vertical-center vertical-center-large background-blue

The biggest benefit of React Native isn't JavaScript. It's **React**.

???
React's architecture.
[http://red-badger.com/blog/2015/03/04/react-native-the-killer-feature-that-nobody-talks-about](http://red-badger.com/blog/2015/03/04/react-native-the-killer-feature-that-nobody-talks-about)

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

???
+ React's component architecture macht es leicht nachzuvollziehen was der Code macht
+ Zukunft: Relay, Flux, ClojureScript
+ **Virtual DOM**: kopiert, **standalone**

---

class: vertical-center background-blue

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
