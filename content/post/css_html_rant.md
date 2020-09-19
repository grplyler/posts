+++
author = "Ryan Plyler"
title = "Quick Rant about CSS grid and when to use it"
date = "2020-09-18"
description = "Quick rant about CSS grid and when to use it"
tags = [
    "css",
    "html",
]
categories = [
    "rants",
    "frontend"
]
draft = true
+++

Can we _please_ use `html` as much as possible for website structure, and _then_
use features of `css` like `flexbox` and `css grid` to _help_ with the struture,
and but lets _stylying_ not _placement_ be the css's primary objective?

For instance, your entire `html` document should _not_ be a bunch of `<divs>` on the
same level that resemble almost nothing of what the final structure of the web page's content
will actually look like, and with `ID`s and `class` names that are generic, numeric, and non-descriptive.

If that is your setup, and you're modeling your structure with almost entirely css
`grid`, `flexbox`, negative and positive `margins` and a bunch of `float` directives,
somethings just not right.

***Instead***

Use HTML to build out the _majority_ of your structure of your webpage. Use _descriptive_
`class` and `id` names. We're humans, not computers, let computers read numbers and ambigous characters.
And structure your html in a such a way that _resembles_ the final look.

Thank you for comming to my Ted Talk.