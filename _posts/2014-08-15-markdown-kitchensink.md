---
layout: post
title:  "Test van syntax highlighting!"
date:   2014-08-15 02:08:13
categories: web
---

Dit is een test van de highlighting...
<!-- more -->
En nog een paragraph

{% highlight javascript linenos%}
'use strict';

var $;

// make Bean and Bonzo use Qwery
// as their internal selector engine
bean.setSelectorEngine(qwery);
bonzo.setQueryEngine(qwery);

(function() {

    $ = function (selector, node) {
        if (node) {
            return bonzo(qwery(selector, node));
        }
        return bonzo(qwery(selector));
    };

    function indexOf (collection, item) {
        for (var i = 0; i < collection.length; i++) {
            if (collection[i] === item) {
                return i;
            }
        }
        return -1;
    }

    // $() will return a bonzo object
    // let's extend bonzo :)
    bonzo.aug({
        // bean events
        on: function () {
            var args = [].slice.call(arguments);
            args.unshift('');
            return this.each(function (elem) {
                args[0] = elem;
                return bean.on.apply(this, args);
            });
        },
        one: function () {
            var args = [].slice.call(arguments);
            args.unshift('');
            return this.each(function (elem) {
                args[0] = elem;
                return bean.one.apply(elem, args);
            });
        },
        off: function () {
            var args = [].slice.call(arguments);
            args.unshift('');
            return this.each(function (elem) {
                args[0] = elem;
                return bean.off.apply(elem, args);
            });
        },
        fire: function () {
            var args = [].slice.call(arguments);
            args.unshift('');
            return this.each(function (elem) {
                args[0] = elem;
                return bean.fire.apply(elem, args);
            });
        },
        // extra functionality
        find: function(s) {
            var r = [],
                i, l, j, k, els;
            for (i = 0, l = this.length; i < l; i++) {
                els = qwery(s, this[i]);
                for (j = 0, k = els.length; j < k; j++) {
                    r.push(els[j]);
                }
            }
            return $(qwery.uniq(r));
        },
        parents: function(selector, closest) {
            // console.log("collection: ",$(selector), selector);
            var collection = $(selector),
                j, k, p, r = [];
            for (j = 0; j < this.length; j++) {
                p = this[j];
                k = p.parentNode;
                while (k) {
                    if (selector && indexOf(collection, k) !== -1) {
                        r.push(k);
                        if (closest) {
                            break;
                        }
                    }else if (!selector){
                        r.push(k);
                    }
                    k = k.parentNode;
                }
            }
            return $(qwery.uniq(r));
        },
        children: function() {
            var i, l, r = [];
            for (i = 0; i < this.length; i++) {
                if (this[i].childNodes){
                    for (l = 0; l < this[i].childNodes.length;l++){
                        if (this[i].childNodes[l].nodeType === 1){
                            r.push(this[i].childNodes[l]);
                        }
                    }
                }
            }
            return $(qwery.uniq(r));
        },
        // siblings: function() {
        //     var i, l, p, r = [];
        //     for (i = 0; i < this.length; i++) {
        //         p = this[i];
        //         l = p.previousSibling;
        //         while (l){
        //             if (l.nodeType === 1){
        //                 r.push(p);
        //             }
        //             l = l.previousSibling;
        //         }
        //         p = this[i];
        //         l = p.nextSibling;
        //         while (l){
        //             if (l.nodeType === 1){
        //                 r.push(l);
        //             }
        //             l = l.nextSibling;
        //         }
        //     }
        //     return $(r);
        // },
        closest: function(selector) {
            return this.parents(selector, true);
        },
        clone: function(deepClone){
            var i = 0,
                r = [],
                div = document.createElement('div'),
                supportsHTML5 = !!document.createElement('canvas').getContext;
            deepClone = deepClone || false;
            for (;i<this.length;i++){
                if (supportsHTML5){
                    r.push(this[i].cloneNode(deepClone));
                }else{
                    div.innerHTML = this[i].outerHTML;
                    r.push(div.firstChild);
                }
            }
            return $(qwery.uniq(r));
        },
        index: function (haystack) {
            haystack = haystack || this.parent().children();
            var needle = this.get(0),
                index = -1,
                i = 0;
            haystack.each(function(elem) {
                if(elem === needle) {
                    index = i;
                }
                i++;
            });
            return index;
        }
    });

    // reqwest
    $.ajax = function(){
        // use reqwest
        reqwest.apply(this, arguments);
    };

    // Arbiter
    $.publish = function(){
        return Arbiter.publish.apply(this, arguments);
    };

    $.subscribe = function(){
        return Arbiter.subscribe.apply(this, arguments);
    };

    $.unsubscribe = function(){
        return Arbiter.unsubscribe.apply(this, arguments);
    };

    $.resubscribe = function(){
        return Arbiter.resubscribe.apply(this, arguments);
    };

    // custom code

    $.parseHTML = function(htmlString){
        var h = document.createElement('div');
        h.innerHTML = htmlString;
        return $(h).children();
    };

    $.template = function(id){

        var temp = $.parseHTML($('template#'+id).html());
        $('[data-id]', temp).each(function(){
            this.id = this.getAttribute('data-id');
        });
        return temp;

    };

    $.serialize = function (form) {
        var q = $.serializeObject(form);
        return q.join('&');
    };

    $.serializeObject = function (form){
        if (!form || form.nodeName !== 'FORM') {
            return;
        }
        var i, j, q = [];
        for (i = form.elements.length - 1; i >= 0; i = i - 1) {
            if (form.elements[i].name === '') {
                continue;
            }
            switch (form.elements[i].nodeName) {
            case 'INPUT':
                switch (form.elements[i].type) {
                case 'checkbox':
                case 'radio':
                    if (form.elements[i].checked) {
                        q.push(form.elements[i].name + '=' + encodeURIComponent(form.elements[i].value));
                    }
                    break;
                case 'file':
                    break;
                default:
                    q.push(form.elements[i].name + '=' + encodeURIComponent(form.elements[i].value));
                }
                break;
            case 'TEXTAREA':
                q.push(form.elements[i].name + '=' + encodeURIComponent(form.elements[i].value));
                break;
            case 'SELECT':
                switch (form.elements[i].type) {
                case 'select-one':
                    q.push(form.elements[i].name + '=' + encodeURIComponent(form.elements[i].value));
                    break;
                case 'select-multiple':
                    for (j = form.elements[i].options.length - 1; j >= 0; j = j - 1) {
                        if (form.elements[i].options[j].selected) {
                            q.push(form.elements[i].name + '=' + encodeURIComponent(form.elements[i].options[j].value));
                        }
                    }
                    break;
                }
                break;
            case 'BUTTON':
                switch (form.elements[i].type) {
                case 'reset':
                case 'submit':
                case 'button':
                    q.push(form.elements[i].name + '=' + encodeURIComponent(form.elements[i].value));
                    break;
                }
                break;
            }
        }
        return q;
    };

    /**
    * $.browser('ie6') to check for current client bowser.
    *
    * @param {String} browser Can be [ie | ie6 | ie7 | ie8 | ie9 | lte7 | lte8 | lte9] or non of them.
    * @return {Boolean} Returns true if browser matches current client browser
    */
    $.browser = function(browser) {
        var browserMetaTag = $('meta[name=browser]')[0],
            browserIdentifiers = [];

        if (typeof browserMetaTag !== 'undefined') {
            browserIdentifiers = browserMetaTag.content.split(' ');

            return indexOf(browserIdentifiers, browser) > -1 ? true : false;
        }

        return false;
    };

    return $;

})();

{% endhighlight %}