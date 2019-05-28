# Culverin

Culverin is a lightweight flex-box framework designed to help with scaffolding responsive layouts. It utlises:

* A 24 column, mobile first grid 
* Simple flex-box container classes
* Justification and alignment 
* rem based padding and margins
* Typography alignment and color, with rem based size and lineheight 


### Breakpoints

* mobile
* touch
* tablet
* laptop
* desktop

Simply use the breakpoint reference by with the relevant column reference:

```html
mobile-24
```

```html
laptop-12
```

Positioning, typography, and margins & padding also react to breakpoints with the addition of the `until` and `from` modifiers. Modifiers are _inclusive_ of the device they reference:

`x-pad-6-until-laptop` would apply _until_ the 'laptop' breakpoint of `1024px`

`font-size-larger-from-desktop` would apply _from_ the 'desktop' breakpoint of `1340px`

Breakpoint classes should be included _after_ any related default classes:

```html
class="oneway-margin-2 oneway-margin-4-from-tablet"
```

### Columns

Culverin offers 24 column classes across 5 breakpoints

* mobile - default 
* touch - from `425px`
* tablet - from `760px`
* laptop - from `1024px`
* desktop - from `1320px`

The responsive width of any element can be specified by appending a breakpoint with the appropraite column reference:  

```html
<article class="mobile-24 tablet-20 laptop-12></article>
```

If the element in question is the direct descendent of a `row`, its defined width should be a fraction of the total viewport width. 
If the element is _not_ the direct descendent of a `row`, its width will be relative to containing parent:

```html
<div class="row">  <!-- 100% viewport width by default -->
  <div class="container 
              mobile-12"> <!-- 50% viewport width -->
    <div class="mobile-24"></div> <!-- 100% of container's width, or 50% of the viewport -->
  </div> 
</div
```

### Containers

Culverin offers three basic, relatively unopinionated 'container' elements, intended to be used as a convenient base.

#### .row

`.row` is intended as a top-level containing element, and occupies 100% of the available (usually the viewport) width.

```css
.row {
  position: relative;
  width: 100%;
  display: flex;
}
```
`.row` prevents wrapping by default. This can be overidden with the `can-wrap` class, and further tailored with the use of breakpoint concious `until` and `from` modifiers:

```html
<!-- forces wrapping after the laptop breakpoint -->
<div class="row can-wrap-from-laptop"></div>
 
<!-- allows wrapping until the tablet breakpoint -->
<div class="row can-wrap-until-tablet</div>
            
```

`.row` elements also accept the `.hidden` class, which in turn accepts the `until` and `from` modifiers:

```html
<div class="row hidden-until-tablet"></div>
```

### .container

The `.container` class is intended as a `<section>` or `<article>` level containing element. It is relatively positioned, allows wrapping, and centers content horizontally by default.

```css
.container {
  position: relative;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
```

`.container` accepts the `.hidden` and `no-wrap` classes, which can be modified in turn with `until` and `from`. Horizontal centering can be overridden by any valid `x-` positioning class such as `x-around`. Positioning classes also accept `until` and `from`, as shown in the example below.

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












