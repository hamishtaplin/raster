Raster is a responsive grid framework written in Sass. Raster is:

- mobile-first responsive
- em-based
- declarative style
- ratio-based
- inline-block based
- compatible with all browsers, including IE7 (IE7 support provided by Javascript)

Raster grid is written in a 'declarative' style meaning that column breakpoints are declared in the markup. There are six main breakpoints, written in 't-shirt size' notation:

## Breakpoints

Breakpoint | Screen minimum width
-----------|----------------------
xs         | 0em
s          | 30em
m          | 45em
l          | 65em
xl         | 95em
xxl        | 120em

Grids are composed of a `.grid` class which acts as a container for columns (`.grid__col`). By default, columns are full-width at all screen sizes, unless specified otherwise. 

The following example demonstrates a simple grid of three columns, full-width by default but switch to thirds at the `m` breakpoint:

```
<div class="grid">
  <div class="grid__col m-1-3">
    <p>Column</p>
  </div>
  <div class="grid__col m-1-3">
    <p>Column</p>
  </div>
  <div class="grid__col m-1-3">
    <p>Column</p>
  </div>
</div>
```

## Ratios

Columns are declared in ratios such as one-half (`1-2`) or two-thirds (`2-3`)—there are a maximum of twelve columns of `1-12`. These ratios are associated with breakpoints via the aforementioned 't-shirt sizes', for example a `.grid__col` of `m-1-3` will be a third of the available width at the `m` breakpoint.

In the following example, we have two columns that change ratio between breakpoints—from full-width (default) to halves at 30em and then thirds at 45em.

```
<div class="grid">
  <div class="grid__col s-1-2 m-1-3">
    <p>This column will be full-width on extra small screens (eg. iPhone) to two columns on small screens (eg. small tablets) to a third on medium screens and above.</p>
  </div>
  <div class="grid__col s-1-2 m-2-3">
    <p>This column will be full-width on extra small screens (eg. iPhone) to two columns on small screens (eg. small tablets) to two-thirds on medium screens and above.</p>
  </div>
</div>
```

## Nesting

Being ratio-based allows easy nesting of columns. In the example below, we can see a grid of two columns, one of which has a sub-grid of another two columns.

```
<div class="grid">
  <div class="grid__col s-1-2">
    <p>This column is one-half at screen sizes above 30em. Nulla vitae elit libero, a pharetra augue. Maecenas sed diam eget risus varius blandit sit amet non magna. Donec sed odio dui.</p>
  </div>
  <div class="grid__col s-1-2">
    <p>This column is also one-half but has a sub-grid of another two columns of half-width.</p>
    <div class="grid">
      <div class="grid__col s-1-2">
        <p>Donec id elit non mi porta gravida at eget metus.</p>
      </div>
      <div class="grid__col s-1-2">
        <p>Duis mollis, est non commodo luctus, nisi erat porttitor ligula, eget lacinia odio sem nec elit.</p>
      </div>
    </div>
  </div>
</div>
```
## Reversible

A reversed grid allows you change the source order of the markup and still keep a left-to-right layout. As you can see in the example below, the columns appear in the reverse order that they occur in the markup:

```
<div class="grid  grid--reverse">
  <div class="grid__col m-1-3">
    <p>1st in the DOM</p>
  </div>
  <div class="grid__col m-2-3">
    <p>2nd in the DOM</p>
  </div>
</div>
```

##Push/Pull

Columns can be pushed or pulled in a particular direction at a specified breakpoint. To reset a push at a subsequent breakpoint, use the `nopush` feature. The following example shows three columns all pushed to the right by one column at the `m` breakpoint. At the `l` breakpoint, the first column has its push removed.

```
<div class="grid">
  <div class="grid__col m-1-4 m-push-1-4 l-nopush">
    <p>Column</p>
  </div>
  <div class="grid__col m-1-4 m-push-1-4">
    <p>Column</p>
  </div>
  <div class="grid__col m-1-4 m-push-1-4">
    <p>Column</p>
  </div>
</div>
```

##Floats

Columns can be collapsed together so that one column will wrap around another—this is useful for maintaing sensible line lengths. In the following example, the text wraps around the image at the `m` breakpoint and then switches to a two-column layout at the `l` breakpoint.

__Note: To wrap a left column around a right column, the right column must come first in the DOM and the `grid--reverse` modifier used to switch them around.

```
<div class="grid grid--reverse">
  <div class="grid__col m-1-4 m-fr">
    <div class="avatar">
      <img src="http://imgsrc.me/200x200/4EA6B8/f3f3f3" width="200" height="200" class="avatar__img">
    </div>
  </div>
  <div class="grid__col m-1-1 l-3-4">
    <div>Aenean eu leo quam. Pellentesque ornare sem lacinia quam venenatis vestibulum. Vestibulum id ligula porta felis euismod semper. Sed posuere consectetur est at lobortis. Vivamus sagittis lacus vel augue laoreet rutrum faucibus dolor auctor. Nullam quis risus eget urna mollis ornare vel eu leo. Praesent commodo cursus magna, vel scelerisque nisl consectetur et. Integer posuere erat a ante venenatis dapibus posuere velit aliquet. Vivamus sagittis lacus vel augue laoreet rutrum faucibus dolor auctor. Aenean eu leo quam. Pellentesque ornare sem lacinia quam venenatis vestibulum. Maecenas faucibus mollis interdum. Nullam quis risus eget urna mollis ornare vel eu leo. Etiam porta sem malesuada magna mollis euismod. Cras justo odio, dapibus ac facilisis in, egestas eget quam. Vivamus sagittis lacus vel augue laoreet rutrum faucibus dolor auctor. Nulla vitae elit libero, a pharetra augue. Curabitur blandit tempus porttitor.</div>
    
  </div>
</div>
```

## Flex

__NOTE: This is an experimental feature and may not work consistently across all browsers.__

The grid can make use of CSS3 capabilities of modern browsers to solve layout problems that were previously unsolvable with CSS alone. A good example of this the ability to have equal-height columns via Flexbox. Simply add `.grid__flex` to any children that are required to be full-height. 

```
<div class="grid  grid--flex">
  <div class="grid__col grid__flex m-1-2">
    <p>Praesent commodo cursus magna, vel scelerisque nisl consectetur et.</p>
  </div>
  <div class="grid__col grid__flex m-1-2">
    <p>Cras justo odio, dapibus ac facilisis in, egestas eget quam. Aenean lacinia bibendum nulla sed consectetur. Donec ullamcorper nulla non metus auctor fringilla. Curabitur blandit tempus porttitor. Maecenas faucibus mollis interdum.</p>
  </div>
</div>
```

*/
