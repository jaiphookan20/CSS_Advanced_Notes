
# CSS Grid Layout

**CSS Grid Layout**  excels at dividing a page into major regions or defining the relationship in terms of size, position, and layer, between parts of a control built from HTML primitives.

Like tables, grid layout enables an author to align elements into columns and rows. However, many more layouts are either possible or easier with CSS grid than they were with tables. For example, a grid container's child elements could position themselves so they actually overlap and layer, similar to CSS positioned elements.

## Basic example[Section](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Grid_Layout#Basic_example)

The example below shows a three-column track grid with new rows created at a minimum of 100 pixels and a maximum of auto. Items have been placed onto the grid using line-based placement.

### HTML[Section](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Grid_Layout#HTML)

```html
<div class="wrapper">
  <div class="one">One</div>
  <div class="two">Two</div>
  <div class="three">Three</div>
  <div class="four">Four</div>
  <div class="five">Five</div>
  <div class="six">Six</div>
</div>
```

### CSS[Section](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Grid_Layout#CSS)

```css
.wrapper {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 10px;
  grid-auto-rows: minmax(100px, auto);
}
.one {
  grid-column: 1 / 3;
  grid-row: 1;
}
.two { 
  grid-column: 2 / 4;
  grid-row: 1 / 3;
}
.three {
  grid-column: 1;
  grid-row: 2 / 5;
}
.four {
  grid-column: 3;
  grid-row: 3;
}
.five {
  grid-column: 2;
  grid-row: 4;
}
.six {
  grid-column: 3;
  grid-row: 4;
}
```

## Syntax[Section](https://developer.mozilla.org/en-US/docs/Web/CSS/grid#Syntax)

```css
/* <'grid-template'> values */
grid: none;
grid: "a" 100px "b" 1fr;
grid: [linename1] "a" 100px [linename2];
grid: "a" 200px "b" min-content;
grid: "a" minmax(100px, max-content) "b" 20%;
grid: 100px / 200px;
grid: minmax(400px, min-content) / repeat(auto-fill, 50px);

/* <'grid-template-rows'> /
   [ auto-flow && dense? ] <'grid-auto-columns'>? values */
grid: 200px / auto-flow;
grid: 30% / auto-flow dense;
grid: repeat(3, [line1 line2 line3] 200px) / auto-flow 300px;
grid: [line1] minmax(20em, max-content) / auto-flow dense 40%;

/* [ auto-flow && dense? ] <'grid-auto-rows'>? /
   <'grid-template-columns'> values */
grid: auto-flow / 200px;
grid: auto-flow dense / 30%;
grid: auto-flow 300px / repeat(3, [line1 line2 line3] 200px);
grid: auto-flow dense 40% / [line1] minmax(20em, max-content);

/* Global values */
grid: inherit;
grid: initial;
grid: unset;
```

### Values[Section](https://developer.mozilla.org/en-US/docs/Web/CSS/grid#Values)

`<'grid-template'>`

Defines the  [`grid-template`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-template "The grid-template CSS property is a shorthand property for defining grid columns, rows, and areas.")  including  [`grid-template-columns`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-template-columns "The grid-template-columns CSS property defines the line names and track sizing functions of the grid columns."),  [`grid-template-rows`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-template-rows "The grid-template-rows CSS property defines the line names and track sizing functions of the grid rows.")  and  [`grid-template-areas`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-template-areas "The grid-template-areas CSS property specifies named grid areas.").

`<'grid-template-rows'> / [ auto-flow && dense? ] <'grid-auto-columns'>?`

Sets up an auto-flow by setting the row tracks explicitly via the  [`grid-template-rows`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-template-rows "The grid-template-rows CSS property defines the line names and track sizing functions of the grid rows.")  property (and the  [`grid-template-columns`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-template-columns "The grid-template-columns CSS property defines the line names and track sizing functions of the grid columns.")  property to  `none`) and specifying how to auto-repeat the column tracks via  [`grid-auto-columns`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-auto-columns "The grid-auto-columns CSS property specifies the size of an implicitly-created grid column track.")  (and setting  [`grid-auto-rows`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-auto-rows "The grid-auto-rows CSS property specifies the size of an implicitly-created grid row track.")  to  `auto`).  [`grid-auto-flow`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-auto-flow "The grid-auto-flow CSS property controls how the auto-placement algorithm works, specifying exactly how auto-placed items get flowed into the grid.")  is also set to  `column`  accordingly, with  `dense`  if it’s specified.

All other  `grid`  sub-properties are reset to their initial values.

`[ auto-flow && dense? ] <'grid-auto-rows'>? / <'grid-template-columns'>`

Sets up an auto-flow by setting the column tracks explicitly via the  [`grid-template-columns`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-template-columns "The grid-template-columns CSS property defines the line names and track sizing functions of the grid columns.")  property (and the  [`grid-template-rows`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-template-rows "The grid-template-rows CSS property defines the line names and track sizing functions of the grid rows.")  property to  `none`) and specifying how to auto-repeat the row tracks via  [`grid-auto-rows`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-auto-rows "The grid-auto-rows CSS property specifies the size of an implicitly-created grid row track.")  (and setting  [`grid-auto-columns`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-auto-columns "The grid-auto-columns CSS property specifies the size of an implicitly-created grid column track.")  to  `auto`).  [`grid-auto-flow`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-auto-flow "The grid-auto-flow CSS property controls how the auto-placement algorithm works, specifying exactly how auto-placed items get flowed into the grid.")  is also set to  `row`  accordingly, with  `dense`  if it’s specified.

All other  `grid`  sub-properties are reset to their initial values.

### Formal syntax[Section](https://developer.mozilla.org/en-US/docs/Web/CSS/grid#Formal_syntax)

[<'grid-template'>](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-template "none | [ <'grid-template-rows'> / <'grid-template-columns'> ] | [ <line-names>? <string> <track-size>? <line-names>? ]+ [ / <explicit-track-list> ]?") [|](https://developer.mozilla.org/en-US/docs/CSS/Value_definition_syntax#Single_bar "Single bar: exactly one of the entities must be present") [<'grid-template-rows'>](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-template-rows "none | <track-list> | <auto-track-list>") / [[](https://developer.mozilla.org/en-US/docs/CSS/Value_definition_syntax#Brackets "Brackets: enclose several entities, combinators, and multipliers to transform them as a single component") auto-flow [&&](https://developer.mozilla.org/en-US/docs/CSS/Value_definition_syntax#Double_ampersand "Double ampersand: all of the entities must be present, in any order") dense[?](https://developer.mozilla.org/en-US/docs/CSS/Value_definition_syntax#Question_mark_() "Question mark: the entity is optional") []](https://developer.mozilla.org/en-US/docs/CSS/Value_definition_syntax#Brackets "Brackets: enclose several entities, combinators, and multipliers to transform them as a single component") [<'grid-auto-columns'>](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-auto-columns "<track-size>+")[?](https://developer.mozilla.org/en-US/docs/CSS/Value_definition_syntax#Question_mark_() "Question mark: the entity is optional") [|](https://developer.mozilla.org/en-US/docs/CSS/Value_definition_syntax#Single_bar "Single bar: exactly one of the entities must be present") [[](https://developer.mozilla.org/en-US/docs/CSS/Value_definition_syntax#Brackets "Brackets: enclose several entities, combinators, and multipliers to transform them as a single component") auto-flow [&&](https://developer.mozilla.org/en-US/docs/CSS/Value_definition_syntax#Double_ampersand "Double ampersand: all of the entities must be present, in any order") dense[?](https://developer.mozilla.org/en-US/docs/CSS/Value_definition_syntax#Question_mark_() "Question mark: the entity is optional") []](https://developer.mozilla.org/en-US/docs/CSS/Value_definition_syntax#Brackets "Brackets: enclose several entities, combinators, and multipliers to transform them as a single component") [<'grid-auto-rows'>](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-auto-rows "<track-size>+")[?](https://developer.mozilla.org/en-US/docs/CSS/Value_definition_syntax#Question_mark_() "Question mark: the entity is optional") / [<'grid-template-columns'>](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-template-columns "none | <track-list> | <auto-track-list>")

## Example[Section](https://developer.mozilla.org/en-US/docs/Web/CSS/grid#Example)

### HTML Content[Section](https://developer.mozilla.org/en-US/docs/Web/CSS/grid#HTML_Content)

```html
<div id="container">
  <div></div>
  <div></div>
  <div></div>
  <div></div>
  <div></div>
  <div></div>
  <div></div>
  <div></div>
</div>
```

### CSS Content[Section](https://developer.mozilla.org/en-US/docs/Web/CSS/grid#CSS_Content)

```css
#container {
  display: grid;
  grid: repeat(2, 60px) / auto-flow 80px;
}

#container > div {
  background-color: #8ca0ff;
  width: 50px;
  height: 50px;
}
```

### Result[Section](https://developer.mozilla.org/en-US/docs/Web/CSS/grid#Result)
