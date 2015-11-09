# scss-grid-mixin
Super easy grid mixin to generate responsive grid.

Class name will .col-X-Y where X it will be the column widht, and Y the columns' number.
You will have for every column a class that add the offset, like .col-offset-X-Y.

## Here the code
```
@mixin generate-grid($columns) {
	@for $i from 1 through $columns {
		$var: ".col-" + $i + "-" + $columns;
		$width: calc(100% / ( #{$columns} / #{$i} ));
		.col-#{$i}-#{$columns} {  
      width: $width;  
    }
    .col-offset-#{$i}-#{$columns} {  
      margin-left: $width;  
    }
  }
}
```

You will just need the code below in your scss file to have 16 columns and offsets.
```
@include generate-grid(16);
```

Working example on [codepen] (http://codepen.io/dbertella/pen/qOJLBJ)
