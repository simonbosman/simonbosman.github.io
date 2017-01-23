---
layout: default
title:  "New website Open Universiteit"
date:   2017-01-23 21:36:00
categories: main
---

I am studying at the Open Universiteit at the Netherlands.<br>
Today they have launched a new website.<br>
The order of the tiles is not how I would like to haven them, so to work...<br>
See the [old layout](https://github.com/simonbosman/simonbosman.github.io/blob/master/content/oldTiles.PNG) 
and the all shiny [new layout](https://github.com/simonbosman/simonbosman.github.io/blob/master/content/newTiles.PNG).

---
I have created the following userscript, so if you want to use it enjoy.
---
{% highlight%}
// ==UserScript==
// @name         Shuffle tiles
// @namespace    http://tampermonkey.net/
// @version      0.1
// @description  shuffle tiles
// @author       simonbosman@gmail.com
// @match        https://mijn.ou.nl/web/ou/home
// @grant        none
// ==/UserScript==

var bootstrap = function(evt){
  if (evt.target.readyState === "complete") { setTimeout(shuffle, 1000); }
};
document.addEventListener('readystatechange', bootstrap, false);

function shuffle() {
    'use strict';
    var tiles = document.getElementsByClassName('v-gridlayout-slot');
    var tileFirstOrg = Array.prototype.filter.call(tiles, function(tile) {
        return tile.innerHTML === '<div class="v-ddwrapper v-widget v-has-width" style="width: 100%;"><div class="v-link v-widget"><a href="http://oustatus.nl/" target="_target"><img class="v-icon" src="https://mijn.ou.nl/html/VAADIN/themes/usertiles/img/oustatus.png"><span></span></a></div></div>';
    });
    var tileSecondOrg = Array.prototype.filter.call(tiles, function(tile) {
        return tile.innerHTML === '<div class="v-ddwrapper v-widget v-has-width" style="width: 100%;"><div class="v-link v-widget"><a href="http://studieplaza.ou.nl" target="_target"><img class="v-icon" src="https://mijn.ou.nl/html/VAADIN/themes/usertiles/img/studieplaza.png"><span></span></a></div></div>';
    });
    var tileFirstNew = Array.prototype.filter.call(tiles, function(tile) {
        return tile.innerHTML === '<div class="v-ddwrapper v-widget v-has-width" style="width: 100%;"><div class="v-link v-widget"><a href="https://youlearn.ou.nl/c/portal/login" target="_blank"><img class="v-icon" src="https://mijn.ou.nl/html/VAADIN/themes/usertiles/img/youlearn.png"><span></span></a></div></div>';
    });
    var tileSecondNew = Array.prototype.filter.call(tiles, function(tile) {
        return tile.innerHTML === '<div class="v-ddwrapper v-widget v-has-width" style="width: 100%;"><div class="v-link v-widget"><a href="https://studienet.ou.nl" target="_blank"><img class="v-icon" src="https://mijn.ou.nl/html/VAADIN/themes/usertiles/img/studienet.png"><span></span></a></div></div>';
    });
    console.log(tileFirstOrg);
    console.log(tileSecondOrg);
    console.log(tileFirstNew);
    console.log(tileSecondNew);
    try {
        var swap1 = tileFirstOrg[0].innerHTML;
        var swap2 = tileSecondOrg[0].innerHTML;
        tileFirstOrg[0].innerHTML = tileFirstNew[0].innerHTML;
        tileSecondOrg[0].innerHTML = tileSecondNew[0].innerHTML;
        tileFirstNew[0].innerHTML = swap1;
        tileSecondNew[0].innerHTML = swap2;
    }
    catch (e) {
        console.log(e);
    }
}
{% endhighlight %}
