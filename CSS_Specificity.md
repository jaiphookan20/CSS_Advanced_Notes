# CSS Specificity

# What is Specificity?

If there are two or more conflicting CSS rules that point to the same element, the browser follows some rules to determine which one is most specific and therefore wins out.

Think of specificity as a score/rank that determines which style declarations are ultimately applied to an element.

The universal selector (*) has low specificity, while ID selectors are highly specific! 

# Specificity Hierarchy
Every selector has its place in the specificity hierarchy. There are four categories which define the specificity level of a selector:

Inline styles - An inline style is attached directly to the element to be styled. Example: <h1 style="color: #ffffff;">.

IDs - An ID is a unique identifier for the page elements, such as #navbar.

Classes, attributes and pseudo-classes - This category includes .classes, [attributes] and pseudo-classes such as :hover, :focus etc.

Elements and pseudo-elements - This category includes element names and pseudo-elements, such as h1, div, :before and :after.

**Specificity**  is the means by which browsers decide which CSS property values are the most relevant to an element and, therefore, will be applied. Specificity is based on the matching rules which are composed of different sorts of  [CSS selectors](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Reference#Selectors).

## How is specificity calculated?[Section](https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity#How_is_specificity_calculated)

Specificity is a weight that is applied to a given CSS declaration, determined by the number of each  [selector type](https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity#Selector_Types)  in the matching selector. When multiple declarations have equal specificity, the last declaration found in the CSS is applied to the element. Specificity only applies when the same element is targeted by multiple declarations. As per CSS rules,  [directly targeted elements](https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity#directly-targeted-elements)  will always take precedence over rules which an element inherits from its ancestor.

**Note:**  [Proximity of elements](https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity#Tree_proximity_ignorance)  in the document tree has no effect on the specificity.

### Selector Types[Section](https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity#Selector_Types)

The following list of selector types increases by specificity:

1.  [Type selectors](https://developer.mozilla.org/en-US/docs/Web/CSS/Type_selectors)  (e.g.,  `h1`) and pseudo-elements (e.g.,  `::before`).
2.  [Class selectors](https://developer.mozilla.org/en-US/docs/Web/CSS/Class_selectors)  (e.g.,  `.example`), attributes selectors (e.g.,  `[type="radio"]`) and pseudo-classes (e.g.,  `:hover`).
3.  [ID selectors](https://developer.mozilla.org/en-US/docs/Web/CSS/ID_selectors)  (e.g.,  `#example`).

Universal selector ([`*`](https://developer.mozilla.org/en-US/docs/Web/CSS/Universal_selectors "The documentation about this has not yet been written; please consider contributing!")), combinators ([`+`](https://developer.mozilla.org/en-US/docs/Web/CSS/Adjacent_sibling_combinator "The documentation about this has not yet been written; please consider contributing!"),  [`>`](https://developer.mozilla.org/en-US/docs/Web/CSS/Child_combinator "The documentation about this has not yet been written; please consider contributing!"),  [`~`](https://developer.mozilla.org/en-US/docs/Web/CSS/General_sibling_combinator "The documentation about this has not yet been written; please consider contributing!"),  ['  '](https://developer.mozilla.org/en-US/docs/Web/CSS/Descendant_combinator),  [`||`](https://developer.mozilla.org/en-US/docs/Web/CSS/Column_combinator "The documentation about this has not yet been written; please consider contributing!")) and negation pseudo-class ([`:not()`](https://developer.mozilla.org/en-US/docs/Web/CSS/:not "The documentation about this has not yet been written; please consider contributing!")) have no effect on specificity. (The selectors declared  _inside_  `:not()`  do, however.)


Inline styles added to an element (e.g.,  `style="font-weight: bold;"`) always overwrite any styles in external stylesheets, and thus can be thought of as having the highest specificity.

### The  `!important`  exception[Section](https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity#The_!important_exception)

When an  `important`  rule is used on a style declaration, this declaration overrides any other declarations. Although technically  `!important`  has nothing to do with specificity, it interacts directly with it. Using  `!important,`  however, is  **bad practice**  and should be avoided because it makes debugging more difficult by breaking the natural  [cascading](https://developer.mozilla.org/en-US/docs/Web/CSS/Cascade)  in your stylesheets. When two conflicting declarations with the  `!important`  rule are applied to the same element, the declaration with a greater specificity will be applied.

**Some rules of thumb:**

-   **Always**  look for a way to use specificity before even considering  `!important`
-   **Only**  use  `!important`  on page-specific CSS that overrides foreign CSS (from external libraries, like Bootstrap or normalize.css).
-   **Never**  use  `!important`  when you're writing a plugin/mashup.
-   **Never**  use  `!important`  on site-wide CSS.

**Instead of using  `!important`, consider:**

1.  Make better use of the CSS cascade
2.  Use more specific rules. By indicating one or more elements before the element you're selecting, the rule becomes more specific and gets higher priority:
    
    ```html
    <div id="test">
      <span>Text</span>
    </div>
    ```
    
    ```css
    div#test span { color: green; }
    div span { color: blue; }
    span { color: red; }
    ```
    
    No matter the order, text will be green because that rule is most specific. (Also, the rule for blue overwrites the rule for red, notwithstanding the order of the rules)
    
3.  As a nonsense special case for (2), duplicate simple selectors to increase specificity when you have nothing more to specify.
    
    ```css
    #myId#myId span { color: yellow; }
    .myClass.myClass span { color: orange; }
    ```



