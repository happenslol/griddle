# Griddle

SASS Mixins for creating flex grids

[![npm](https://img.shields.io/npm/v/griddle-sass.svg)](https://www.npmjs.com/package/dragtime)
[![Downloads per month](https://img.shields.io/npm/dm/griddle-sass.svg)](https://www.npmjs.com/package/dragtime)

![quote logo](https://raw.githubusercontent.com/happenslol/griddle/master/assets/logo.png?raw=true)

Griddle provides the following mixins:

### Waffle grid
This allows you to make a "waffle"-style grid, where every element has the same width and elements in every row have the same height. To use it, simply import griddle and apply the mixin to the container:

```scss
@import "griddle-sass";

.container {
    @include grid-waffle($cols: 4);
}
```

You can optionally pass `$gutter-width` and `$gutter-height`. It will default to `1em` if you don't pass anything.

The above code will result in the following when the class is applied to a container with several `div`s inside:

![quote example waffle](https://raw.githubusercontent.com/happenslol/griddle/master/assets/example1.png?raw=true)

### Class grid
A class grid lets you define several percentages, and will then generate classes for you that you can apply to whatever element you want. Do not that they still need to be within the container where you use the mixin. For every row, you will also need to mark the first and last element with `first` and `last` respectively.

SCSS:
```scss
.container {
    @include grid-classes("1/10", "1/5", "3/10", "1/3", "2/5", "1/2");
}
```

HTML:
```html
<div class="container">
    <div class="1/2 first"></div>
    <div class="1/2 last"></div>

    <div class="1/3 first"></div>
    <div class="1/3"></div>
    <div class="1/3 last"></div>

    <div class="1/10 first"></div>
    <div class="1/5"></div>
    <div class="2/5"></div>
    <div class="3/10 last"></div>
</div>
```

This is what the result looks like:

![quote example class](https://raw.githubusercontent.com/happenslol/griddle/master/assets/example2.png?raw=true)

### Template grid
Inspired directly by the grid template syntax, this lets you visually define zones for your grid. This is best when you know ahead of time exactly how many elements there will be and how they will be scaled in relation to each other.  
No additional markup is needed except for the class on the conntainer.

```scss
.template-grid {
    @include grid-template(
        "    1/2     1/2    ",
        "1/3     1/3     1/3",
        "1/10 2/10 4/10 3/10",
        "   1/3     2/3     "
    );
}
```

This results in the following:

![quote example template](https://raw.githubusercontent.com/happenslol/griddle/master/assets/example3.png?raw=true)

Please check the examples to see everything in action!