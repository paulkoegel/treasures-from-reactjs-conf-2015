class: title
background-image: url(images/tarkovsky3.jpg)

.titles[
# Treasures from<br>React.js Conf 2015

.author[
  Paul Wittmann &mdash; [@wakkahari](https://twitter.com/wakkahari)
]]

???
Railslove
JavaScript, Ruby, Clojure

---

class: react-conf
background-image: url(images/react-conf.png)

???
+ 28./29. Januar in SF
+ Neugier wecken und neue Ideen vorstellen
+ Überblick über neuste Entwicklungen, zeigen warum React gerade so Wellen schlägt

---

# React ❤ Simplicity

+ makes us _think_ & challenges us
--

+ embraces JavaScript
--

+ easy to reason about
--

+ component architecture
--

+ rendering is an implementation detail

???
React begeistert mich weil man ihm/ihr anmerkt, dass sie nach Einfachheit strebt und dabei neue Wege aufzeigt wie man UIs bauen kann - hat _alle_ anderen JS Lösungen beeinflusst.
+ gibt uns zu denken - fordert uns heraus - wir entdecken immer noch erst die Möglichkeiten die uns durch seine Ideen eröffnet werden
+ nimmt JS begeistert an und nutzt es wo's nur geht
+ was passiert (Verhalten/Programmfluss) ist leicht nachzuvollziehen / macht was man erwartet
+ modular, LEGO, nicht verknotet (-> einfach), unidirektionaler Datenfluss: Kindkomponenten erhalten Daten von Eltern aber nicht umgekehrt
+ virtueller DOM: DOM wird für mich wegabstrahiert

---

# Contents

1. Introduction to React
2. Treasure Time

---

class: background-cover where-we-stand
background-image: url(images/Ricoh-GR-sample-images-3.jpg)

# Where we stand

???
User Interfaces sind schwer
JS frameworks sprießen aus dem Boden Blogpost

---

.vertical-center[
HTML wasn't built for web apps
]

---

1. jQuery: DOM as data store
2. Backbone: JavaScript data as single source of truth
3. Ember, Angular
4. React

???
Ember, Angular: easy - focus on programmer convenience, abstractions leak through, have to go at great lengths, not elegant under the hood
React: simple, abstractions don't leak through, easy to grasp, easy to reason about. elegance and simplicity > programmer convenience.
not a framework but part of a fexible toolbox

framework — A product with the business logic removed, but all of the assumptions left in.
[Devil’s Dictionary of Programming](http://programmingisterrible.com/post/65781074112/devils-dictionary-of-programming)

---

JavaScript data -> DOM

prismatic example from Ian Davis

---

Problems:

+ how to keep everything in synch?
+ how to keep things performant?
  -> precise DOM updates

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

.vertical-center[
React is all about components
]

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
---

# React

```javascript
var = React.createClass({

});

```

???
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

---

# React Native

???
Virtual DOM - doesn't matter where you're actually rendering - can easily be exchanged

---

# GraphQL & Relay

---

# Hotloader
https://www.youtube.com/watch?v=pw4fKkyPPg8

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

class: what-is-react
background-image: url(images/rat_tribe_zhang_hai_hai.jpg)

.overlay[
# 0. What is React?
]

---

.vertical-center[
<a href="http://localhost:8080/02-1-magic-move" target="_blank">
  Magic Move
</a>
]

---

???
+ JavaScript Bibliothek von Facebook um User Interfaces zu bauen.
+ steckt in: Facebook, Instagram, Atom Editor, Flipboard, Airbnb, Atlassian Hipchat
+ kein MVC, "das _V_ in MVC"
+ funktional geprägt
+ inpsiriert von Rich Hickeys Einfachheitsbegriff (cf. [Simplicity matters](https://www.youtube.com/watch?v=rI8tNMsozo0))

---

.vertical-center[
  JavaScript _library_ for building UIs
]

---

# Logo Farm

???
more: https://github.com/facebook/react/wiki/Sites-Using-React

---

component with JSX example

render method calls functions, embraces JS and its data structures - doesn't need models ("React quickly became known as the 'V' in MVC and people kept asking what do I use for the 'M' then? The answer is you don't need an 'M', you have JavaScript arrays and objects already.")

---

props and state
shared mutable state is the root of all evil

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

background-image: url(images/sunshine.jpg)

???
:)

---

.vertical-center.large[
Questions
]

---

# Links
+ [React.js Conf 2015 Videos](https://www.youtube.com/playlist?list=PLb0IAmt7-GS1cbw4qonlQztYV1TAW0sCr)
+ [Removing User Interface Complexity, or Why React is Awesome](http://jlongster.com/Removing-User-Interface-Complexity,-or-Why-React-is-Awesome)
+ [React’s diff algorithm](http://calendar.perfplanet.com/2013/diff)
+ [Coming to React from Angular](http://www.stridenyc.com/blog/2015/3/4/coming-to-react-from-angular)

---

class: code-fullscreen component-example

### JSX

```javascript
render: function() {
  return <div>
    <div>{ this.state.count }</div>
    <button onClick={ this.addOne }> +1 </button>
  </div>
}
```

<hr>

### Becomes

```javascript
render: function() {
  return React.DOM.div(null,
    React.DOM.div(null, this.state.count),
    React.DOM.button({ onClick: this.addOne }, '+1')
  );
}
```

???
JSX is a very thin layer on top of JavaScript.

---
class: no-vertical-padding
.contain-images[
![](images/alman-rethink-best-practices.png)
![](images/alman-today.png)
]
https://twitter.com/cowboy/status/339858717451362304
