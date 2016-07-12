---
layout: post
title:  "Time to settle on some sort of structure for CSS"
date:   2016-07-12 18:27:00 +0800
categories: css sass web-dev
---

Recently I realised that I didn't actually have a very sure way of organising my CSS code. Having fallen for Sass quite hard     but not too long ago, I was still quite enamoured with being able to nestle properties away, into what I found to be a very intuitive form. And I never really found too much issue with picking up older Sass code and understanding what was going on, or tracking properties back from the webpage to the stylesheet. 

But recently I've been working on a couple of projects which, for reasons too tedious to go into, I haven't had Sass available, and I've begun to find myself flailing a little without that crutch. So it seems a good time to settle on some sort of set of rules for myself to better organise my CSS code, with the primary intention of writing raw CSS that is easier to understand and maintain, and secondarily to perhaps improve the Sass code I was writing.

I hadn't really realised that this was a fairly hot topic, bubbling around for last couple of years with various proposals for how to do just this, ranging from very prescriptive rules and frameworks, through to "yeah, it's nice when you do x, because it let's you do y" observations and articles. It seems since [Smacss](https://smacss.com/) was published by Jonathan Snook back in 2011(?), the subject has never really been off the table for discussion - right up to articles such as ["Is 2016 the year of Atomic CSS?"](http://www.creativebloq.com/css3/atomic-css-11619006) looking at Atomic CSS (which as far as I can tell originates in about 2014). 

*Incidentally, to my briefly judgemental eye, Atomic CSS seems a little bit awful. I **think** I can see the point - abstracting a property itself allows one to reduce the repetition of defining that property a fair amount: instead of multiple classes having `float:left` set, for example, you can just apply a `float-left` class, which defines it just once. My issue comes with adding all those style-specific classes, most of which will likely just be defining a single style, being so close to just applying styles directly to an HTML element to make me shudder. Perhaps I've misunderstood, or perhaps I've missed some change in attitudes that means this isn't such a bad thing anymore...* 

Rather than list pros and cons of verious approaches here, I am just going to list my current approach, and expect this post to be updated as this approach evolves. So...

## [Atomic Design](http://bradfrost.com/blog/post/atomic-web-design/) by Brad Frost 

Reading this for the first time was one of those crystalisation moments. It describes (just about) the approach I've been taking already to structuring a page - how it breaks into it's constituent elements - but with an analogy that just seems to settle it all into place. So: 

Atoms < Molecules < Organisms < Templates < Pages

and for example:

Search Button < Button, Text Box, Prompt < Search Molecule, Navigation, Logo < Header, Main Body, Footer < Home Page 

## [BEM](http://getbem.com/) by Yandex

A naming convention to enable easier re-ingestion of old CSS. Blocks, Elements, Modifiers.

- A **block** is an entity that is meaningful on it's own - perhaps a `nav` element.
- An **element** is a part of a block which would make no sense on it's own - an item in a navigation list, for example.
- A **modifier** is a flag on a block or element to effect some change - e.g. a navigation item is active.

The only thing that made me slightly wary with BEM was an aesthetic concern about the style convention for naming these elements, as follows:

`block`  
`block__element`  
`block__element--modifier`  

All those double-dashes and double-underscores ('dunderscores'?) make me wince, but I suppose one just has to suck that up every so often for the sake of other people understanding your code...

And writing the Sass for this can be pretty neat:

```
block{
    &__element{
        &--modifier{

        }  
    }
}
```

