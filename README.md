# scss-grid-mixin
Super easy grid mixin to generate responsive grid.

Class name will .col-X-Y where X it will be the column widht, and Y the columns' number.
You will have for every column a class that add the offset, like .col-offset-X-Y.

## Here the code
```
@mixin generate-grid($columns, $size: '') {
  @for $i from 1 through $columns {
    $width: calc(100% / ( #{$columns} / #{$i} ));
    @if($size == '') {
      .col-#{$i}-#{$columns} {
        width: $width;
      }
      .col-offset-#{$i}-#{$columns} {
        margin-left: $width;
      }
    }
    @else {
      .col-#{$size}-#{$i}-#{$columns} {
        width: $width;
      }
      .col-#{$size}-offset-#{$i}-#{$columns} {
        margin-left: $width;
      }
    }
  }
}

```

You will just need the code below in your scss file to have 16 columns and offsets.
```
@include generate-grid(16);
```
You can even set a size in bootstrap style, something like 'md' or 'lg' and add your grid in a media query. 
The final classes name will be col-md-1-16 and col-md-offset-1-16

```
@media (min-width: 768px) {
  @include generate-grid(16, 'md');
}
```

Working example on [codepen] (http://codepen.io/dbertella/pen/qOJLBJ)
