# Stylus Plus
**Handy stylus mixins**

## Quick Start

To use, simplely do `@import "stylus-plus/lib"`. Everything is indexed in reasonable order.

Rather, if you prefer fine control over what to use, import modules as it pleases you. Each module is designed to work independently, but just keep in mind that some of them rely on default variables, e.g., the "border" module.


## Docs

### border

`border` default to `1px solid $border-color`, where `$border-color = #767676`, which is configurable in `border.styl`. Supply any one or more of the 3 values will override default values.

```
// defaults
border()
=> border: 1px solid $border-color;

// 1 argument
border(red)
=> border: 1px solid #f00;

border(2px)
=> border: 2px solid $border-color;

// 2 arguments, order doesn't matter
border(dotted 2px)
=> border: 2px dotted $border-color;

// sided border property follows same rule
border-left()
=> border-left: 1px solid $border-color;

// and here comes the shorthands
border-lr()
=> border-left: 1px solid $border-color;
   border-right: 1px solid $border-color;
```

### colors

For those who are familiar with Photoshop HSB color, use `hsb($hue, $saturation, $brightness)` to define colors. 

```
color: hsb(10, 100, 100)
=> color: #ff2b00;

// if alpha value is supplied, will return rgba instead of hex.
color: hsb(10, 100, 100, 0.8)
=> color: rgba(255,43,0,0.8);
```

Use `grey($percentage)` [alias: `gray($percentage)`] to define greyscales.

```
color: grey(20)
=> color: #333;
```

### position

`relative(), absolute(), fixed()` as 3 shorthands mixins for `position` property. Following examples illustrate with `relative()`, same rules apply to `aboslute()` and `fixed()`.

```
relative()
=> position: relative;

relative(0)
=> position: relative;
   top: 0;
   right: 0;
   bottom: 0;
   left: 0;
   
relative(10px 20px)
=> position: relative;
   top: 10px;
   right: 20px;
   bottom: 10px;
   left: 20px;

relative(10px 20px 15px)
=> position: relative;
   top: 10px;
   right: 20px;
   bottom: 15px;
   left: 20px;

relative(10px 20px 15px)
=> position: relative;
   top: 10px;
   right: 20px;
   bottom: 15px;
   left: 20px;

relative(10px 20px 15px 5px)
=> position: relative;
   top: 10px;
   right: 20px;
   bottom: 15px;
   left: 5px;

// use "$side $unit" pair to specify which side to apply
relative(bottom 10px)
=> position: relative;
   bottom: 10px;

relative(top 10px bottom 5px)
=> position: relative;
   top: 10px;
   bottom: 5px;

// omitted unit defaults to "0"
relative(top bottom)
=> position: relative;
   top: 0;
   bottom: 0;

relative(top left 5px)
=> position: relative;
   top: 0;
   left: 5px;
```