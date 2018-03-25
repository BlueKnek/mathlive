# Basic Example

This example shows how to interact with a MathLive math field.

It uses the minified version of the MathLive library.

## Load the stylesheets
Load both the "core" and regular stylesheet. The "core" stylesheet contains
only the basic to display a simple formula. You can lazily load the 
regular stylesheet, but you will need both to display correctly formulas.

```html
<link rel="stylesheet" href="../../dist/mathlive.core.css">
<link rel="stylesheet" href="../../dist/mathlive.css">
```

## Load the Javascript library
Preferably at the end of your page, before the `</body>` tag, to avoid 
blocking rendering.

```html
<script src="../../dist/mathlive.js"></script>
```

## Interact with a math field

Create a math field from an element on page. Here we used a `<div>` element 
with an ID of `mf`. If the element has any textual content, it will be used 
as the initial content of the math field.

Now is also a good time to customize the math field. Here, we'll provide a 
handler to be notified when the content of the math field has changed, for 
example when the user types something in the field.

```javascript
    const mf = MathLive.makeMathField('mf', {
        onContentDidChange: updateOutput
    });
```

We'll process that notification by extracting a LaTeX representation from the 
math field, and displaying it in an output element.

```javascript
    function updateOutput(mathfield) {
        document.getElementById('output').innerHTML = mathfield.latex();
    }
```