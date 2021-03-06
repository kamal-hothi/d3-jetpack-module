# d3-jetpack-module

[d3-jetpack](https://github.com/gka/d3-jetpack) and [d3-starterkit](https://github.com/1wheel/d3-starterkit) updated to use the [D3 4.0 module pattern](https://bost.ocks.org/mike/d3-plugin/). 

## Installing

If you use NPM, `npm install d3-jetpack-module`. Otherwise, download the latest [d3v4+jetpack.js](https://raw.githubusercontent.com/1wheel/d3/jetpack/build/d3v4%2Bjetpack.js).

## Documentation

coming soon! So far there are only minor changes from jetpack and starterkit: 

<a name="st" href="#st">#</a> selection.<b>st</b>(<i>name[, value]</i>) [<>](https://github.com/1wheel/d3-jetpack-module/blob/master/src/st.js "Source")

Works like d3v3's `.attr`. Passing an object to name sets multiple attributes, passing a string returns a single attribute and passing a string & second argument sets a single attribute.

To avoid having to use quotes around attributes and styles with hyphens when using the object notation, camelCase keys are hyphenated. Instead of:

    selection
        .style('stroke-width', 10)
        .style('text-anchor', 'end')
        .style('font-weight', 600)

or with [d3-selection-multi](https://github.com/d3/d3-selection-multi): 

    selection.styles({'stroke-width': 10, 'text-anchor': 'end', 'font-weight': 600})

you can write: 

    selection.st({fontSize: 10, textAnchor: 'end', fontWeight: 600})

With syntax highlighting on, it is a little easier to see the difference between keys and values when everything isn't a string. Plus there's less typing! 


<a name="at" href="#at">#</a> selection.<b>at</b>(<i>name[, value]</i>) [<>](https://github.com/1wheel/d3-jetpack-module/blob/master/src/at.js "Source")

Like `at`, but for `style`. Additionally, when a number is passed to a style that requires a unit of measure, like `margin-top` or `font-size`, `px` is automatically appended. Instead of 

    selection
        .style('margin-top', height/2 + 'px')
        .style('font-size', '40px')
        .style('width', width - 80 + 'px')

The `+ px`s can also be dropped: 

    selection.st({marginTop: height/2, fontSize: 40, width: width - 80})

`at` and `st` do not work on transitions.

<a name="selectAppend" href="#selectAppend">#</a> d3.<b>selectAppend</b>(<i>selector</i>) [<>](https://github.com/1wheel/d3-jetpack-module/blob/master/src/selectAppend.js "Source")

Selects the first element that matches the specified selector string or if no elements match the selector, it will append an element. This is often handy for elements which are required as part of the DOM hierachy, especially when making repeated calls to the same code. When appending it will also add id and classes, same as Jetpack's [append](#append)

```js
d3.selectAppend('ul.fruits')
    .selectAll('li')
    .data(data)
```

