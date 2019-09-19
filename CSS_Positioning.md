
# CSS Positioning

The whole idea of positioning is to allow us to override the basic document flow behavior described above, to produce interesting effects. What if you want to slightly alter the position of some boxes inside a layout from their default layout flow position, to give a slightly quirky, distressed feel? Positioning is your tool. Or if you want to create a UI element that floats over the top of other parts of the page, and/or always sits in the same place inside the browser window no matter how much the page is scrolled? Positioning makes such layout work possible.

There are a number of different types of positioning that you can put into effect on HTML elements. To make a specific type of positioning active on an element, we use the  [`position`](https://developer.mozilla.org/en-US/docs/Web/CSS/position "The position CSS property sets how an element is positioned in a document. The top, right, bottom, and left properties determine the final location of positioned elements.")  property.

## Static positioning

Static positioning is the default that every element gets — it just means "put the element into its normal position in the document layout flow — nothing special to see here."

To demonstrate this, and get your example set up for future sections, first add a  `class`  of  `positioned`  to the second  [`<p>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/p "The HTML <p> element represents a paragraph.")  in the HTML:

```html
<p class="positioned"> ... </p>
```

Now add the following rule to the bottom of your CSS:

```css
.positioned {
  position: static;
  background: yellow;
}
```

If you now save and refresh, you'll see no difference at all, except for the updated background color of the 2nd paragraph. This is fine — as we said before, static positioning is the default behavior!

**Note**: You can see the example at this point live at  `[1_static-positioning.html](http://mdn.github.io/learning-area/css/css-layout/positioning/1_static-positioning.html)`  ([see source code](https://github.com/mdn/learning-area/blob/master/css/css-layout/positioning/1_static-positioning.html)).

## Relative positioning

Relative positioning is the first position type we'll take a look at. This is very similar to static positioning, except that once the positioned element has taken its place in the normal layout flow, you can then modify its final position, including making it overlap other elements on the page. Go ahead and update the  `position`  declaration in your code:

```css
position: relative;
```

If you save and refresh at this stage, you won't see a change in the result at all. So how do you modify the element's position? You need to use the  [`top`](https://developer.mozilla.org/en-US/docs/Web/CSS/top "The top CSS property participates in specifying the vertical position of a positioned element. It has no effect on non-positioned elements."),  [`bottom`](https://developer.mozilla.org/en-US/docs/Web/CSS/bottom "The bottom CSS property participates in setting the vertical position of a positioned element. It has no effect on non-positioned elements."),  [`left`](https://developer.mozilla.org/en-US/docs/Web/CSS/left "The left CSS property participates in specifying the horizontal position of a positioned element. It has no effect on non-positioned elements."), and  [`right`](https://developer.mozilla.org/en-US/docs/Web/CSS/right "The right CSS property participates in specifying the horizontal position of a positioned element. It has no effect on non-positioned elements.")  properties, which we'll explain in the next section.

## Introducing top, bottom, left, and right

[`top`](https://developer.mozilla.org/en-US/docs/Web/CSS/top "The top CSS property participates in specifying the vertical position of a positioned element. It has no effect on non-positioned elements."),  [`bottom`](https://developer.mozilla.org/en-US/docs/Web/CSS/bottom "The bottom CSS property participates in setting the vertical position of a positioned element. It has no effect on non-positioned elements."),  [`left`](https://developer.mozilla.org/en-US/docs/Web/CSS/left "The left CSS property participates in specifying the horizontal position of a positioned element. It has no effect on non-positioned elements."), and  [`right`](https://developer.mozilla.org/en-US/docs/Web/CSS/right "The right CSS property participates in specifying the horizontal position of a positioned element. It has no effect on non-positioned elements.")  are used alongside  [`position`](https://developer.mozilla.org/en-US/docs/Web/CSS/position "The position CSS property sets how an element is positioned in a document. The top, right, bottom, and left properties determine the final location of positioned elements.")  to specify exactly where to move the positioned element to. To try this out, add the following declarations to the  `.positioned`  rule in your CSS:

```html
top: 30px;
left: 30px;
```

**Note**: The values of these properties can take any  [units](https://developer.mozilla.org/en-US/docs/Learn/CSS/Introduction_to_CSS/Values_and_units)  you'd logically expect — pixels, mm, rems, %, etc.

## Definition and Usage

The  `position`  property specifies the type of positioning method used for an element (static, relative, absolute, fixed, or sticky).

Default value:

static

Inherited:

no

Animatable:

no.  [Read about  _animatable_](https://www.w3schools.com/cssref/css_animatable.asp)

Version:

CSS2

JavaScript syntax:

_object_.style.position="absolute"

## CSS Syntax

position: static|absolute|fixed|relative|sticky|initial|inherit;

## Property Values

Value

Description

Play it

static

Default value. Elements render in order, as they appear in the document flow

[Play it »](https://www.w3schools.com/cssref/playit.asp?filename=playcss_position)

absolute

The element is positioned relative to its first positioned (not static) ancestor element

[Play it »](https://www.w3schools.com/cssref/playit.asp?filename=playcss_position&preval=absolute)

fixed

The element is positioned relative to the browser window

[Play it »](https://www.w3schools.com/cssref/playit.asp?filename=playcss_position&preval=fixed)

relative

The element is positioned relative to its normal position, so "left:20px" adds 20 pixels to the element's LEFT position

[Play it »](https://www.w3schools.com/cssref/playit.asp?filename=playcss_position&preval=relative)

sticky

The element is positioned based on the user's scroll position

A sticky element toggles between  `relative`  and  `fixed`, depending on the scroll position. It is positioned relative until a given offset position is met in the viewport - then it "sticks" in place (like position:fixed).

**Note:**  Not supported in IE/Edge 15 or earlier. Supported in Safari from version 6.1 with a -webkit- prefix.

[Try it »](https://www.w3schools.com/cssref/tryit.asp?filename=trycss_position_sticky)

initial

Sets this property to its default value.  [Read about  _initial_](https://www.w3schools.com/cssref/css_initial.asp)

[Play it »](https://www.w3schools.com/cssref/playit.asp?filename=playcss_position&preval=initial)

inherit

Inherits this property from its parent element.  [Read about  _inherit_](https://www.w3schools.com/cssref/css_inherit.asp)

----------

## More Examples

### Example

How to position an element relative to its normal position:

h2.pos_left  {  
position:  relative;  
left:  -20px;  
}  
  
h2.pos_right  {  
position:  relative;  
left:  20px;  
}
