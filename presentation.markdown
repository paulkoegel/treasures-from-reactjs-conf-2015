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

User Interfaces sind schwer
JS frameworks sprießen aus dem Boden Blogpost

React:
- Rendering und Datenstrukturen sind Implementierungsdetails
  saubere, flexible Plattform auf die es aufzubauen lohnt
- geht mehr darum die Ideen zu vermitteln - wenn ihr alle morgen anfangt React zu nutzen bin ich sehr froh, aber wenn ihr immutable.js oder [virtual-dom](https://github.com/Matt-Esch/virtual-dom) in euren Projekten einsetzt bin ich auch froh :)

---

class: react-conf
background-image: url(images/react-conf.png)

???
+ 28./29. Januar in SF
+ Neugier wecken und neue Ideen vorstellen
+ Überblick über neuste Entwicklungen, zeigen warum React gerade so Wellen schlägt

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

.vertical-center-wrapper[
.vertical-center[
<a href="http://localhost:8080/02-1-magic-move" target="_blank">
  Magic Move
</a>
]]

---

???
+ JavaScript Bibliothek von Facebook um User Interfaces zu bauen.
+ steckt in: Facebook, Instagram, Atom Editor, Flipboard, Airbnb, Atlassian Hipchat
+ kein MVC, "das _V_ in MVC"
+ funktional geprägt
+ inpsiriert von Rich Hickeys Einfachheitsbegriff (cf. [Simplicity matters](https://www.youtube.com/watch?v=rI8tNMsozo0))

---

.vertical-center-wrapper[
  .vertical-center[
    JavaScript _library_ for building UIs
]]

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

.vertical-center-wrapper[
.vertical-center[
.large[
Questions
]]]

---

# Links

+ [React.js Conf 2015 Videos](https://www.youtube.com/playlist?list=PLb0IAmt7-GS1cbw4qonlQztYV1TAW0sCr)
+ [Removing User Interface Complexity, or Why React is Awesome](http://jlongster.com/Removing-User-Interface-Complexity,-or-Why-React-is-Awesome)

+ [React’s diff algorithm](http://calendar.perfplanet.com/2013/diff)
