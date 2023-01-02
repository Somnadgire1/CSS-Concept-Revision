# CSS-Concept-Revision
1. What is CSS and how does it work with HTML?
(Cascading Style Sheets) allows you to create great-looking web pages, CSS is a language for specifying how documents are presented to users — how they are styled, laid out, etc.
CSS style sheet can contain rules that affect the styling of multiple pages on a site. When any one of those pages are visited, the style sheet code is accessed, and it determines how the HTML that makes up the page is displayed.

2. What are selectors and what are their different types?
A CSS selector selects the HTML element(s) for styling purpose. CSS selectors select HTML elements according to its id, class, type, attribute etc.
Types - 
Element Selector
Id Selector
Class Selector
Universal Selector
Group Selector
Attribute Selector
Pseudo-Class Selector
Pseudo-Element Selector

3. What is CSS selector specificity and how does it work?
Selector Specificity in CSS is a relative measure of how specific a CSS selector is in the way it targets an HTML element. It is used in the Specificity algorithm to determine the final CSS property values for a given element in the DOM.
The Specificity algorithm calculates the weight of a CSS selector based on a set of three-column values. Each column represents a category of selectors in terms of how specifically they target an element.

4. Describe z-index and how stacking context is formed.
The z-index property in CSS controls the vertical stacking order of elements that overlap. z-index only affects elements that have a position value which is not static.

Without any z-index value, elements stack in the order that they appear in the DOM (the lowest one down at the same hierarchy level appears on top). Elements with non-static positioning (and their children) will always appear on top of elements with default static positioning, regardless of HTML hierarchy.

A stacking context is an element that contains a set of layers. Within a local stacking context, the z-index values of its children are set relative to that element rather than to the document root. Layers outside of that context — i.e. sibling elements of a local stacking context — can't sit between layers within it. If an element B sits on top of element A, a child element of element A, element C, can never be higher than element B even if element C has a higher z-index than element B.
Each stacking context is self-contained - after the element's contents are stacked, the whole element is considered in the stacking order of the parent stacking context. A handful of CSS properties trigger a new stacking context, such as opacity less than 1, filter that is not none, and transform that is notnone.


5. Describe BFC (Block Formatting Context) and how it works.
A Block Formatting Context (BFC) is part of the visual CSS rendering of a web page in which block boxes are laid out. Floats, absolutely positioned elements, inline-blocks, table-cells, table-captions, and elements with overflow other than visible (except when that value has been propagated to the viewport) establish new block formatting contexts.

Knowing how to establish a block formatting context is important, because without doing so, the containing box will not contain floated children. This is similar to collapsing margins, but more insidious as you will find entire boxes collapsing in odd ways.

6. Have you ever used a grid system, and if so, what do you prefer?
Before Flex became popular (around 2014), the float-based grid system was the most reliable because it still has the most browser support among the alternative existing systems (flex, grid). Bootstrap was using the float approach until Bootstrap 4 which switched to the flex-based approach. As of writing (2020), flex is the recommended approach for building grid systems and has decent browser support.
For the adventurous, they can look into CSS Grid Layout, which uses the shiny new grid property; it is even better than flex for building grid layouts and will be the de facto way to do so in the future.

7. Have you used or implemented media queries or mobile specific layouts/CSS?
Yes. An example would be transforming a stacked pill navigation into a fixed-bottom tab navigation beyond a certain breakpoint.

8. Explain how a browser determines what elements match a CSS selector.
This part is related to the above about writing efficient CSS. Browsers match selectors from rightmost (key selector) to left. Browsers filter out elements in the DOM according to the key selector and traverse up its parent elements to determine matches. The shorter the length of the selector chain, the faster the browser can determine if that element matches the selector.

For example with this selector p span, browsers firstly find all the <span> elements and traverse up its parent all the way up to the root to find the <p> element. For a particular <span>, as soon as it finds a <p>, it knows that the <span> matches and can stop its matching.

9. Describe pseudo-elements and discuss what they are used for.
A CSS pseudo-element is a keyword added to a selector that lets you style a specific part of the selected element(s). They can be used for decoration (:first-line, :first-letter) or adding elements to the markup (combined with content: ...) without having to modify the markup (:before, :after).

:first-line and :first-letter can be used to decorate text.
Used in the .clearfix hack as shown above to add a zero-space element with clear: both.
Triangular arrows in tooltips use :before and :after. Encourages separation of concerns because the triangle is considered part of styling and not really the DOM.

10. Explain your understanding of the box mode.
The CSS box model describes the rectangular boxes that are generated for elements in the document tree and laid out according to the visual formatting model. Each box has a content area (e.g. text, an image, etc.) and optional surrounding padding, border, and margin areas.

11. What does * { box-sizing: border-box; } do? What are its advantages?
By default, elements have box-sizing: content-box applied, and only the content size is being accounted for.
box-sizing: border-box changes how the width and height of elements are being calculated, border and padding are also being included in the calculation.
The height of an element is now calculated by the content's height + vertical padding + vertical border width.
The width of an element is now calculated by the content's width + horizontal padding + horizontal border width.
Taking into account paddings and borders as part of our box model resonates better with how designers actually imagine content in grids.


12. What is the CSS display property and can you give a few examples of its use?
none, block, inline, inline-block, flex, grid, table, table-row, table-cell, list-item.
a)none: Does not display an element (the element no longer affects the layout of the document). All child element are also no longer displayed. The document is rendered as if the element did not exist in the document tree.
b)block: The element consumes the whole line in the block direction (which is usually horizontal).
c)inline: Elements can be laid out beside each other.
d)inline-block: Similar to inline, but allows some block properties like setting width and height.
e)table: Behaves like the <table> element.
f)table-row: Behaves like the <tr> element
g)table-cell: Behaves like the <td> element
h)list-item: Behaves like a <li> element which allows it to i)define list-style: type and list-style-position

13. What's the difference between inline and inline-block?
Parameter           inline					                    inline-block
a)Can specify       i)No. Will ignore if being set.             i)Yes
width and 
height	
b)Margins           ii)Only horizontal sides respected. 	    ii)All sides respected.
and paddings

14. What's the difference between the "nth-of-type()" and "nth-child()" selectors?
nth-child():
It is a paragraph element
It is the second child of a parent.
nth-of-type():
Select the second paragraph child of a parent.

15. What's the difference between a relative, fixed, absolute and statically positioned element?
a) static - The default position; the element will flow into the page as it normally would. The top, right, bottom, left and z-index properties do not apply.
b) relative - The element's position is adjusted relative to itself, without changing layout (and thus leaving a gap for the element where it would have been had it not been positioned).
c) absolute - The element is removed from the flow of the page and positioned at a specified position relative to its closest positioned ancestor if any, or otherwise relative to the initial containing block. Absolutely positioned boxes can have margins, and they do not collapse with any other margins. These elements do not affect the position of other elements.
d) fixed - The element is removed from the flow of the page and positioned at a specified position relative to the viewport and doesn't move when scrolled.

16. What existing CSS frameworks have you used locally, or in production? How would you change/improve them?
Bootstrap - Slow release cycle. Bootstrap 4 has been in alpha for almost 2 years. Add a spinner button component, as it is widely used.
Semantic UI - Source code structure makes theme customization extremely hard to understand. Its unconventional theming system is a pain to customize. Hardcoded config path within the vendor library. Not well-designed for overriding variables unlike in Bootstrap.
Bulma - A lot of non-semantic and superfluous classes and markup required. Not backward compatible. Upgrading versions breaks the app in subtle manners.

17. Have you used CSS Grid?
Yes. Which uses the shiny new grid property; it is even better than flex for building grid layouts and will be the de facto way to do so in the future.