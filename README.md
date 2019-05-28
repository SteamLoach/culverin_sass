# Culverin

Culverin is a lightweight flex-box framework designed to help with scaffolding responsive layouts. It utlises:

* A 24 column, mobile first grid 
* Simple flex-box container classes
* Justification and alignment 
* rem based padding and margins
* Typography alignment and color, with rem based size and lineheight 


#### Breakpoints

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
