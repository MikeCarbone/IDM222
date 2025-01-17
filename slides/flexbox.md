build-lists: true
footer: IDM 221: Web Authoring II
slidenumbers: true
autoscale: true
theme: Cobalt2, 1

# IDM 222

## Web Design II

### Flexbox
### Mr. Professor Mike Carbone

---

# Objectives

- Introduce Flexbox
- Implement Flexbox

---

# Objective

## Introduce Flexbox

---

![100%](https://spin.atomicobject.com/wp-content/uploads/20160615142357/flexbox-animation.gif)

^ The _Flexbox Layout_ (Flexible Box) module (currently a W3C Last Call Working Draft) aims at providing a more efficient way to lay out, align and distribute space among items in a container, even when their size is unknown and/or dynamic (thus the word "flex").

^ The main idea behind the flex layout is to give the container the ability to alter its items' width/height (and order) to best fill the available space (mostly to accommodate to all kind of display devices and screen sizes). A flex container expands items to fill available free space, or shrinks them to prevent overflow.

---

![100%](https://www.bram.us/wordpress/wp-content/uploads/2016/10/fukol-demo.gif)

^ Most importantly, the flexbox layout is direction-agnostic as opposed to the regular layouts (block which is vertically-based and inline which is horizontally-based). While those work well for pages, they lack flexibility (no pun intended) to support large or complex applications (especially when it comes to orientation changing, resizing, stretching, shrinking, etc.).

^ Let's begin by learning the terminology associated with flexbox.

---

![fit](http://digm.drexel.edu/crs/IDM222/presentations/images/flexbox-base.png)

^ Since flexbox is a whole module and not a single property, it involves a lot of things including its whole set of properties. Some of them are meant to be set on the container (parent element, known as "flex container") whereas the others are meant to be set on the children (said "flex items").

---

![fit](http://digm.drexel.edu/crs/IDM222/presentations/images/flexbox-main_axis.png)

^ **main axis** - The main axis of a flex container is the primary axis along which flex items are laid out. Beware, it is not necessarily horizontal; it depends on the `flex-direction` property (see below).

---

![fit](http://digm.drexel.edu/crs/IDM222/presentations/images/flexbox-main_startend.png)

^ **main-start | main-end** - The flex items are placed within the container starting from main-start and going to main-end.

---

![fit](http://digm.drexel.edu/crs/IDM222/presentations/images/flexbox-main_size.png)

^ **main size** - A flex item's width or height, whichever is in the main dimension, is the item's main size. The flex item's main size property is either the `width` or `height` property, whichever is in the main dimension.

---

![fit](http://digm.drexel.edu/crs/IDM222/presentations/images/flexbox-cross_axis.png)

^ **cross axis** - The axis perpendicular to the main axis is called the cross axis. Its direction depends on the main axis direction.

---

![fit](http://digm.drexel.edu/crs/IDM222/presentations/images/flexbox-cross_startend.png)

^ **cross-start | cross-end** - Flex lines are filled with items and placed into the container starting on the cross-start side of the flex container and going toward the cross-end side.

---

![fit](http://digm.drexel.edu/crs/IDM222/presentations/images/flexbox-cross_size.png)

^ **cross size** - The width or height of a flex item, whichever is in the cross dimension, is the item's cross size. The cross size property is whichever of `width` or `height` that is in the cross dimension

---

# Objective

## Implement Flexbox

---

## Properties for the Parent

### (flex container)

![inline](http://digm.drexel.edu/crs/IDM222/presentations/images/flexbox-parent.png)

^ First let's talk about the flex container, also know as the parent container; in this example, the purple box.

---

### `display`

```css
.container {
  display: flex; /* or inline-flex */
}
```

^ This defines a flex container, inline or block depending on the given value. It enables a flex context for **all** its _direct_ children.

---

### `flex-direction`

![inline](http://digm.drexel.edu/crs/IDM222/presentations/images/flex-direction.png)

^ The `flex-direction` property establishes the main-axis, thus defining the direction flex items are place in the flex container. Flexbox is a single-direction layout concept. Think of flex items as primarily laying out either in horizontal rows or vertical columns.

---

### `flex-direction` Syntax

```css
.container {
  flex-direction: row | row-reverse | column | column-reverse;
}
```

^ `row` (default): left to right

^ `row-reverse`: right to left

^ `column`: top to bottom

^ `column-reverse`: bottom to top

---

### `flex-wrap`

![inline](http://digm.drexel.edu/crs/IDM222/presentations/images/flex-wrap.png)

^ By default, flex items will all try to fit onto one line. You can change that and allow the items to wrap as needed with this property. Direction also plays a role here, determining the direction new lines are stacked in.

---

### `flex-wrap` Syntax

```css
.container {
  flex-wrap: nowrap | wrap | wrap-reverse;
}
```

^ `nowrap` (default): single-line

^ `wrap`: multi-line

^ `wrap-reverse`: multi-line in opposite direction

---

### `flex-flow`

```css
.container {
  flex-flow: flex-direction | flex-wrap;

  /* example */
  flex-flow: row nowrap; /* default */
}
```

^ This is a shorthand `flex-direction` and `flex-wrap` properties, which together define the flex container's main and cross axes. Default is `row nowrap`.

---

### `justify-content`

![inline](http://digm.drexel.edu/crs/IDM222/presentations/images/justify-content.png)

^ This defines the alignment along the main axis. It helps distribute extra free space left over when either all the flex items on a line are inflexible, or are flexible but have reached their maximum size. It also exerts some control over the alignment of items when they overflow the line.

---

### `justify-content` Syntax

```css
.container {
  justify-content: flex-start
                   flex-end
                   center
                   space-between
                   space-around
}
```

^ flex-start (default): items are packed toward the start line

^ flex-end: items are packed toward to end line

^ center: items are centered along the line

^ space-between: items are evenly distributed in the line; first item is on the start line, last item on the end line

^ space-around: items are evenly distributed in the line with equal space around them. Note that visually the spaces aren't equal, since all the items have equal space on both sides. The first item will have one unit of space against the container edge, but two units of space between the next item because that next item has its own spacing that applies.

---

### `align-items`

![inline](http://digm.drexel.edu/crs/IDM222/presentations/images/align-items.png)

^ This defines the default behavior for how flex items are laid out along the cross axis on the current line. Think of it as the `justify-content` version for the cross-axis (perpendicular to the main-axis).

---

### `align-items` Syntax

```css
.container {
  align-items: flex-start
               flex-end
               center
               baseline
               stretch
}
```

^ flex-start: cross-start margin edge of the items is placed on the cross-start line

^ flex-end: cross-end margin edge of the items is placed on the cross-end line

^ center: items are centered in the cross-axis

^ baseline: items are aligned such as their baselines align

^ stretch (default): stretch to fill the container (still respect min-width/max-width)

---

### `align-content`

![inline](http://digm.drexel.edu/crs/IDM222/presentations/images/align-content.png)

^ This aligns a flex container's lines within when there is extra space in the cross-axis, similar to how `justify-content` aligns individual items within the main-axis.

---

### `align-content` Syntax

```css
.container {
  align-content: flex-start
                 flex-end
                 center
                 space-between
                 space-around
                 stretch
}
```

^ `flex-start`: lines packed to the start of the container

^ `flex-end`: lines packed to the end of the container

^ `center`: lines packed to the center of the container

^ `space-between`: lines evenly distributed; the first line is at the start of the container while the last one is at the end

^ `space-around`: lines evenly distributed with equal space around each line

^ `stretch` (default): lines stretch to take up the remaining space

---

## Properties for the Children

### flex items

![inline](http://digm.drexel.edu/crs/IDM222/presentations/images/flexbox-parent.png)

---

### `order`

![inline](http://digm.drexel.edu/crs/IDM222/presentations/images/order.png)

^ By default, flex items are laid out in the source order. However, the `order` property controls the order in which they appear in the flex container.

---

### `order` Syntax

```css
.item {
  order: <integer>;
}
```

---

### `flex-grow`

![inline](http://digm.drexel.edu/crs/IDM222/presentations/images/flex-grow.png)

^ This defines the ability for a flex item to grow if necessary. It accepts a unitless value that serves as a proportion. It dictates what amount of the available space inside the flex container the item should take up.

---

### `flex-grow` Syntax

```css
.item {
  flex-grow: <number>; /* default 0 */
}
```

^ If all items have `flex-grow` set to 1, the remaining space in the container will be distributed equally to all children. If one of the children has a value of 2, the remaining space would take up twice as much space as the others (or it will try to, at least). Negative numbers are invalid.

---

### `flex-shrink`

```css
.item {
  flex-shrink: <number>; /* default 1 */
}
```

^ This defines the ability for a flex item to shrink if necessary. Negative numbers are invalid.

---

### `flex-basis`

```css
.item {
  flex-basis: <length> | auto; /* default auto */
}
```

^ This defines the default size of an element before the remaining space is distributed. It can be a length (e.g. 20%, 5rem, etc.) or a keyword. The `auto` keyword means "look at my width or height property" (which was temporarily done by the `main-size` keyword until deprecated). The `content` keyword means "size it based on the item's content" - this keyword isn't well supported yet, so it's hard to test and harder to know what its brethren `max-content`, `min-content`, and `fit-content` do.

---

### `flex`

```css
.item {
  flex: none | [ <'flex-grow'> <'flex-shrink'> | <'flex-basis'> ]

  /* example */
  flex: 0 1 auto; /* default */
}
```

^ This is the shorthand for `flex-grow`, `flex-shrink` and `flex-basis` combined. The second and third parameters (`flex-shrink` and `flex-basis`) are optional. Default is `0 1 auto`.

---

### `align-self`

![inline](http://digm.drexel.edu/crs/IDM222/presentations/images/align-self.png)

^ This allows the default alignment (or the one specified by `align-items`) to be overridden for individual flex items.

---

### `align-self` Syntax

```css
.item {
  align-self: auto
              flex-start
              flex-end
              center
              baseline
              stretch
}
```

^ Please see the align-items explanation to understand the available values.

---

## No Effect

- `float`
- `clear`
- `vertical-align`

---

> Example Time

^ _examples/flexbox_

---

## Can I Use It

[Can I Use It?](http://caniuse.com/#search=flex)

---

# Let's Play

![flexbox frog](http://digm.drexel.edu/crs/IDM222/presentations/images/flexboxfroggy.png)

[Flexbox Froggy](http://flexboxfroggy.com)

^ Examples and concepts pulled from [css-tricks.com](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
