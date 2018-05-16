# Pasting through Javascript

CutBox will allow you to paste through a Javascript function.

## How do I paste through Javascript?

To send your paste through javascript, select one or more item(s) in
CutBox and press **Cmd** + **Enter**

## Add functions to `~/.cutbox.js`

Cutbox will read from `~/.cutbox.js` when it starts

You can **Reload Javascript** in the CutBox's
Javascript preferences.

CutBox will look for functions added to (`cutboxFunctions`).

See bolow:

```javascript
var mapFn = items => items.map(e => e )
var joinFn = items => items.join(items.length > 0 ? "\n" : "")

// After function definitions...

var cutboxFunctions = [
  {
    name: "Join",
    key: "j", // Shortcut key
    map: mapFn 
  },
  {
    name: "Join spaced",
    key: "s",
    join: join 
  },
]
```

## Defining functions

CutBox accepts two types of function

Maps and Joins.

Maps will 

- accept a single argument, an array of strings `[String]`
- return an array of strings `-> [String]`

Here's a simple example of a map function in Javascript ES6:

```javascript
var fn = items => items.map( e => `"${e}"` )
```

Joins will

- accept a single argument, an array of strings `[String]`
- return a string `-> String`

Here's a simple example of a join function in Javascript ES6:

```javascript
var fn = items => items.join()
```

`fn` reads items and joins them into a single string.

## Some examples

CutBox will let you do anything you want with the text it's about to
paste.

*Here's a few examples:*

Squeeze text to just one space between words.

```js
var squeeze = items => items.map(s => s.replace(/\s+/g, ' ')
                            .join(items.length > 0 ? "\n" : "")
```

Turn this:

```
My    example text   has    too    many      spaces
```

into this...

```
My example text has too many spaces
```

Quote selected items

```js
var  = items => items.map(s => `"${s}"`)
                     .join(items.length > 0 ? "\n" : "")
```

Turn this:

```
My text
```

into this...

```
"My text"
```

or turn this:

```
My selected item
Another one
etc
```

into this...

```
"My selected item"
"Another one"
"etc"
```

Quote and comma separate:

```js
var  = items => (items.map(s => `"${s}"`))
                      .join(items.length > 0 ? ", " : "")
```

turn this:

```
My selected item
Another one
etc
```

into this...

```
"My selected item", "Another one", "etc"
```
