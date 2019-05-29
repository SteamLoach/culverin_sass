# Culverin

Culverin is a lightweight flex-box framework designed to help with scaffolding responsive layouts. It utlises:

* A 24 column, mobile first grid 
* Simple flex-box container classes
* Justification and alignment 
* rem based padding and margins
* Typography alignment and color, with rem based size and lineheight 

### Responsive Classes

Culverin uses 5 breakpoint references:

* mobile - default 
* touch - from `425px`
* tablet - from `760px`
* laptop - from `1024px`
* desktop - from `1320px`

In addition to numbered 'column' width classes (`.mobile-24`, `.laptop-12`, etc) most container, position, typography, margin, and padding classes also react to breakpoints with the addition of the `-until` and `-from` modifiers. 

`x-pad-6-until-laptop` would apply _until_ the 'laptop' breakpoint of `1024px`

`font-size-larger-from-desktop` would apply _from_ the 'desktop' breakpoint of `1340px`


Modifiers are _inclusive_ of the device they reference, and should be included _after_ any related default classes:

```html
<div class="wrapper oneway-margin-2 oneway-margin-4-from-tablet"></div>

<div class="container x-around-from-laptop"></div>
```

### Columns

Culverin offers 24 column classes across 5 breakpoints

* mobile - default 
* touch - from `425px`
* tablet - from `760px`
* laptop - from `1024px`
* desktop - from `1320px`

The responsive width of any element can be specified by appending a breakpoint with the appropriate column reference:  

```html
<article class="mobile-24 
                tablet-20
                laptop-12></article>
```

If the element in question is the direct descendent of a `.row`, its defined width should be a fraction of the total viewport width. 
If the element is _not_ the direct descendent of a `.row`, its width will be relative to containing parent:

```html
<div class="row">  <!-- 100% viewport width by default -->
  <div class="container 
              mobile-12"> <!-- 50% viewport width -->
    <div class="mobile-24"></div> <!-- 100% of container's width, or 50% of the viewport -->
  </div> 
</div
```

### Containers

Culverin offers three basic, relatively unopinionated 'container' elements, intended to be used as a convenient base. They are, in loose order of heirarchy:

1 - `.row`
2 - `.container`
3 - `.wrapper`

A simple usecase might be:

```html
<section class="row x-center">
  <article class="container x-around y-center mobile-18">
    <div class="wrapper mobile-16">
    ...
    </div>
    <div class="wrapper mobile-8">
    ...
    </div>
  </article>
</section>
```

#### .row

`.row` is intended as a top-level containing element, and occupies 100% of the available (usually the viewport) width.

```css
.row {
  position: relative;
  width: 100%;
  display: flex;
}
```
`.row` prevents wrapping by default. This can be overidden with the `.can-wrap` class, and further tailored with the use of breakpoint concious `-until` and `-from` modifiers:

```html
<!-- forces wrapping after the laptop breakpoint -->
<div class="row can-wrap-from-laptop"></div>
 
<!-- allows wrapping until the tablet breakpoint -->
<div class="row can-wrap-until-tablet</div>
            
```

`.row` elements also accept the `.hidden` class, which in turn accepts the `-until` and `-from` modifiers:

```html
<div class="row hidden-until-tablet"></div>
```

#### .container

The `.container` class is intended as a `<section>` or `<article>` level containing element. It is relatively positioned, allows wrapping, and centers content horizontally by default.

```css
.container {
  position: relative;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
```

`.container` accepts the `.hidden` and `.no-wrap` classes, which can be modified in turn with `-until` and `-from`. Horizontal centering can be overridden by any valid `.x-` positioning class such as `.x-around`. Positioning classes also accept `until` and `-from`, as shown in the example below.

```html
<div class="row can-wrap x-center">
  <article class="container 
                  mobile-22 
                  laptop-18 x-around-from-laptop"></article>
  <article class="container 
                  mobile-12
                  hidden-from-tablet"></article>
</div>
```

####.wrapper

`.wrapper` is a loose catch-all class for turning any element into a flex-container. `.wrapper` allows wrapping by default, and accepts the `.hidden` and `.no-wrap` classes (with optional `-until` and `-from` modifiers) in the same way as `.container`. 

`.wrapper` also takes the `.is-absolute` class, applying absolulte position in relation to the containing parent. Both `.row` and `.container` elements are relatively positioned by default so as to provide a reference for descendent `.wrapper is-absolute` elements.
`is-absolute` accepts `-from` and `-until` modifiers, eg: `.is-absolute-until-tablet`.










