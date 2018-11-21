
## CSS questions

[1. CSS selectors, explain what does the below mean:](https://github.com/mirlz/low-level-front-end-interview-questions/blob/master/css.md/#1-css-selectors-explain-what-does-the-below-mean)
	
    .a
    #a
    [type=text]
    *a 
    a

[2. Which / what element is targeted from below: ](https://github.com/mirlz/low-level-front-end-interview-questions/blob/master/css.md/#2-which-what-element-is-targeted-from-below)

    .a, .b
    .a .b 
    .a > .b
    .a ~ .b
    .a + .b

[3. What's the difference between the position values: `static`, `relative`, `absolute`, `fixed` ](https://github.com/mirlz/low-level-front-end-interview-questions/blob/master/css.md/#3-whats-the-difference-between-the-position-values)

[4. What does the `flex` property in CSS do?](https://github.com/mirlz/low-level-front-end-interview-questions/blob/master/css.md/#4-what-does-the-flex-property-in-css-do)

-----

### 1. CSS selectors, explain what does the below mean:
	
    .a //class
    #a // identifier
    [type=text] //target elements with attribute type of text
    * //selects all elements, usually put on top of CSS file for default
    a // target all hyperlinks
    
### 2. Which / what element is targeted from below: 

    i) .a, .b
    ii) .a .b 
    iii) .a > .b
    iv) .a ~ .b
    v) .a + .b

i) elements with class of 'a' and 'b'

ii) elements with class of 'b' and contained in elements with class of 'a'

iii) direct descendant with class of 'b' contained in elements with class of 'a'

iv) target siblings with class of 'a' and 'b', does **not need to be direct adjacent**, as long as it's on the same level

v) only elements with class of 'a' and 'b' that are **directly adjacent** 

### 3. What’s the difference between the position values:  `static`,  `relative`,  `absolute`,  `fixed`

-   `static`: every element has a static position by default, so the element will stick to the normal page flow. So if there is a  [left](http://css-tricks.com/almanac/properties/l/left/)/[right](https://css-tricks.com/almanac/properties/r/right/)/[top](https://css-tricks.com/almanac/properties/t/top/)/[bottom](https://css-tricks.com/almanac/properties/b/bottom/)/[z-index](http://css-tricks.com/almanac/properties/z/z-index/)  set then there will be no effect on that element.
-   `relative`: an element’s original position remains in the flow of the document, just like the  `static`  value. But now  [left](http://css-tricks.com/almanac/properties/l/left/)/[right](https://css-tricks.com/almanac/properties/r/right/)/[top](https://css-tricks.com/almanac/properties/t/top/)/[bottom](https://css-tricks.com/almanac/properties/b/bottom/)/[z-index](http://css-tricks.com/almanac/properties/z/z-index/)  will work. The positional properties “nudge” the element from the original position in that direction.
-   `absolute`: the element is removed from the flow of the document and other elements will behave as if it’s not even there whilst all the other positional properties will work on it.
-   `fixed`: the element is removed from the flow of the document like absolutely positioned elements. In fact they behave almost the same, only fixed positioned elements are always relative to the document, not any particular parent, and are unaffected by scrolling.

_Sources_

 - https://css-tricks.com/almanac/properties/p/position/

### 4. What does the `flex` property in CSS do?

The **`flex`**  [CSS](https://developer.mozilla.org/en-US/docs/CSS "CSS") property sets how a flex item will grow or shrink to fit the space available in its flex container. It is a [shorthand](https://developer.mozilla.org/en-US/docs/Web/CSS/Shorthand_properties) for [`flex-grow`](https://developer.mozilla.org/en-US/docs/Web/CSS/flex-grow "The flex-grow CSS property specifies the flex grow factor of a flex item. It specifies how much of the available space in the flex container should be assigned to that item. If all sibling items have the same flex grow factor, then all items will receive the same share of available space, otherwise it is distributed according to the ratio defined by the different flex grow factors."), [`flex-shrink`](https://developer.mozilla.org/en-US/docs/Web/CSS/flex-shrink "The flex-shrink CSS property specifies the flex shrink factor of a flex item. Flex items will shrink to fill the container according to the flex-shrink number, when the default size of flex items is larger than the flex container."), and [`flex-basis`](https://developer.mozilla.org/en-US/docs/Web/CSS/flex-basis "The flex-basis CSS property sets the initial main size of a flex item. It sets the size of the content box unless otherwise set with box-sizing.").

_Sources_

- https://developer.mozilla.org/en-US/docs/Web/CSS/flex
- https://philipwalton.github.io/solved-by-flexbox/
