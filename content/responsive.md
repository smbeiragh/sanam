## Responsive
Developing responsive website using pure media queries is not scalable even in website with few pages.

1. using pure media queries is not scalable
2. final code is not readable enough
3. designers and developers communication is not easy
4. changing a breakpoint is painful

To address this issues, Sanam recommends use of named breakpoints and an API e.g. a mixin via a pre-processor
 languages e.g. SASS.
 
For example we can define a set of variables or a sass map as reference of named breakpoints and a mixin
as API that gets breakpoint names or variables and writes media queries for us. we also can use libraries like
[SASS-MQ](https://github.com/sass-mq/sass-mq)

**example**
Using mixin and sass map, you can read more about this topic on this [great article](http://www.sitepoint.com/managing-responsive-breakpoints-sass/)
```SCSS
$breakpoints: (
  'small'  : ( min-width:  767px ),
  'medium' : ( min-width:  992px ),
  'large'  : ( min-width: 1200px )
);
 
@mixin respond-to($name) {
  // If the key exists in the map
  @if map-has-key($breakpoints, $name) {
    // Prints a media query based on the value
    @media #{inspect(map-get($breakpoints, $name))} {
      @content;
    }
  }

  // If the key doesn't exist in the map
  @else {
    @warn "Unfortunately, no value could be retrieved from `#{$breakpoint}`. "
        + "Please make sure it is defined in `$breakpoints` map.";
  }
}

// usage
@include respond-to(small) { ... }
@include respond-to(medium) { ... }
@include respond-to(large) { ... }
``` 