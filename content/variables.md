## Variables
Sanam Uses Following syntax for defining variables. all following parts are camelCase

```css
<propertyName>-<value[Name|Hint]>[--componentName[__elementName[--modifierName]]]
```

Example:
```css
// gray color of copyright element of footer component 
$color-gray--footer__copyrigth

// z-index of container element of nav componnent
$zIndex-1--nav__container
```

This syntax has several benefits:

1. great auto complete by IDE, for example when you are going to set a color
 by typing color IDE will show a list of all color variable
2. property name and value name give us a good idea about what this variable
 contains
3. component naming part tells where this variable is used if bounded to a component. 

## Colors
Sanam Organize colors in four different categories

1. pallet colors
2. gray scale colors
3. semantic colors
4. brand colors

Colors are one of types that can go out of control easily, managing number 
of colors can help reduce styles size. To mange colors applying all colors
must be done via variables, also using an API like a SASS function can be
useful but simplicity in this area can be more useful. Sanam suggests simple
variables because:

1. variables are easier to locate and search
2. variables lets us benefit IDE auto complete

### colors formatting
Sanam promotes use of hsl(hue, saturation, lightness) color format, hsl format is

1. more understandable and meaningful to humans
2. easier to notice un-intended color changes in contrast with hex and rgba
3. easier to compare colors and shades

### color shades
Sanam suggest to provide a set of shades of every color using semantic names like
base, dark and darker and stick to use this pre-defined shades.
sometimes we need to create an extra shade of a defined color which is not 
pre-defined in variable in such cases we can use helper function to apply a custom
shade or alpha chanel, but this cases should be minor. if it often happens it 
may you should re-tune pre-defined shades or add a few more shades as predefined
and don't let number of colors go out of control.

## Pallet Colors
Base on colors theory there are four type color pallets.

1. *Mono color* with a single primary color
2. *Adjacent colors* and *Triad colors* with one primary color and two secondary colors)
3. *Tetrad* colors with four colors, one primary color and two secondary colors plus
 a complement color

Sanam define four different color name as primary, secondary1, secondary2 and a 
complement for the maximum number of colors and semantic names for several shades
of each color. base on variable naming convention an example may look like as following

```scss

$color-primary--lightest:  hsl(192, 90%, 70%);
$color-primary--lighter:   hsl(192, 90%, 60%);
$color-primary--light:     hsl(192, 90%, 50%);
$color-primary--base:      hsl(192, 90%, 40%);
$color-primary--dark:      hsl(192, 90%, 30%);
$color-primary--darker:    hsl(192, 90%, 20%);
$color-primary--darkest:   hsl(192, 90%, 10%);

$color-secondary1--lightest:  hsl(230, 90%, 70%);
$color-secondary1--lighter:   hsl(230, 90%, 60%);
$color-secondary1--light:     hsl(230, 90%, 50%);
$color-secondary1--base:      hsl(230, 90%, 40%);
$color-secondary1--dark:      hsl(230, 90%, 30%);
$color-secondary1--darker:    hsl(230, 90%, 20%);
$color-secondary1--darkest:   hsl(230, 90%, 10%);

$color-secondary2--lightest:  hsl(180, 90%, 70%);
$color-secondary2--lighter:   hsl(180, 90%, 60%);
$color-secondary2--light:     hsl(180, 90%, 50%);
$color-secondary2--base:      hsl(180, 90%, 40%);
$color-secondary2--dark:      hsl(180, 90%, 30%);
$color-secondary2--darker:    hsl(180, 90%, 20%);
$color-secondary2--darkest:   hsl(180, 90%, 10%);

$color-complement--lightest:  hsl(10, 90%, 70%);
$color-complement--lighter:   hsl(10, 90%, 60%);
$color-complement--light:     hsl(10, 90%, 50%);
$color-complement--base:      hsl(10, 90%, 40%);
$color-complement--dark:      hsl(10, 90%, 30%);
$color-complement--darker:    hsl(10, 90%, 20%);
$color-complement--darkest:   hsl(10, 90%, 10%);

```

## Gray Shades
Gray shades in most projects can get crazy very easily, Ideally having five
different shades plus one white and black is enough but most designers are
picky about colors specially about gray shades. they would like to tune them
test them and so on. this can very easily end up to having lots of gray shades
in a small project. it's enough to have five or seven gray shades like pallet colors
but if you think that's not working for you, Sanam recommends using variable names
with color code in their names. By doing this next time we try to apply a new gray
shade IDE will show us list of all defined shades and we can chose to add 
a new shade or pike one of pre-defined shades. In case of not using IDE,
preprocessor will complain about undefined variable and we will notice, then
we can check our predefined gray variable to decide to define new variable or
pike an old one.
Also we can analyse gray shades usage to minimize and re-tune them later. 

Example:
```scss
// basic solustion
$color-white: #fff;
$color-black: #000;
$color-gray--lightest:  #eee;
$color-gray--lighter:   #aaa;
$color-gray--light:     #666;
$color-gray--base:      #444;
$color-gray--dark:      #222;
$color-gray--darker:    #111;
$color-gray--darkest:   #000;

// advance solution for complex projects
$color-gray-f-f: #ffffff;
$color-gray-f-5: #f5f5f5;
$color-gray-f-0: #f0f0f0;
$color-gray-e-e: #eeeeee;
// .... lots of other variables
$color-gray-7-a: #7a7a7a;
$color-gray-7-0: #707070;
$color-gray-4-4: #444444;
$color-gray-1-1: #111111;
$color-gray-0-0: #000000;

```

## Semantic Colors
Semantic colors are useful in conveying concepts like danger, failure, success and so on.
it's about human common sense about specific colors, commonly we use red, green, blue,
yellow or orange for these concepts. Saname suggests to define a set of color variables
to maintain this colors to keep them separate from pallet colors. we may assign a
color of pallet to a semantic color variables or tune them based on color palette. defining
separate set of variable for semantic colors help to keep track or semantic colors while 
changing or re-tuning color pallet.

```scss

$color-success--lightest:  hsl(121, 90%, 70%);
$color-success--lighter:   hsl(121, 90%, 60%);
$color-success--light:     hsl(121, 90%, 50%);
$color-success--base:      hsl(121, 90%, 40%);
$color-success--dark:      hsl(121, 90%, 30%);
$color-success--darker:    hsl(121, 90%, 20%);
$color-success--darkest:   hsl(121, 90%, 10%);

$color-info--lightest:  hsl(200, 90%, 70%);
$color-info--lighter:   hsl(200, 90%, 60%);
$color-info--light:     hsl(200, 90%, 50%);
$color-info--base:      hsl(200, 90%, 40%);
$color-info--dark:      hsl(200, 90%, 30%);
$color-info--darker:    hsl(200, 90%, 20%);
$color-info--darkest:   hsl(200, 90%, 10%);

$color-warning--lightest:  hsl(38, 90%, 70%);
$color-warning--lighter:   hsl(38, 90%, 60%);
$color-warning--light:     hsl(38, 90%, 50%);
$color-warning--base:      hsl(38, 90%, 40%);
$color-warning--dark:      hsl(38, 90%, 30%);
$color-warning--darker:    hsl(38, 90%, 20%);
$color-warning--darkest:   hsl(38, 90%, 10%);

$color-danger--lightest:  hsl(1, 90%, 70%);
$color-danger--lighter:   hsl(1, 90%, 60%);
$color-danger--light:     hsl(1, 90%, 50%);
$color-danger--base:      hsl(1, 90%, 40%);
$color-danger--dark:      hsl(1, 90%, 30%);
$color-danger--darker:    hsl(1, 90%, 20%);
$color-danger--darkest:   hsl(1, 90%, 10%);

```

## Brand Colors
Sometimes branding colors may differ from color pallet in such cases we should
define branding colors as variable, like pallet colors branding colors may include
several shades.

``` scss

$color-brandGreen--lightest:  hsl(121, 90%, 70%);
$color-brandGreen--lighter:   hsl(121, 90%, 60%);
$color-brandGreen--light:     hsl(121, 90%, 50%);
$color-brandGreen--base:      hsl(121, 90%, 40%);
$color-brandGreen--dark:      hsl(121, 90%, 30%);
$color-brandGreen--darker:    hsl(121, 90%, 20%);
$color-brandGreen--darkest:   hsl(121, 90%, 10%);

```

## Z-index Scale
Z-index values can go out of control very easy. Even in small projects z-index headache is common.
Setting arbitrary numbers on z-index and inspecting everything to make sure everything is working
is'nt scalable even on small projects. Defining all z-index values in a single file can help us to
keep an eye on all layers and their situation relative to each other. 
based on [this article](https://medium.com/@fat/mediums-css-is-actually-pretty-fucking-good-b8e2a6c78b06#.c6i9flixv)
every z-index value should be defined in z-index file using following syntax:

```scss
$zIndex-level--componentName[__elementName[--modifierName]|[--modifierName]]
```
   
Level is a number between 1 and 10 that refers to teen private levels of z-index. they are private
variables to z-index scale file and should't be use directly out side of that file.

An example from one of my latest projects:
```scss
// provide bird eye view of all layers

// Z-Index Scale (private vars)
// --------------------------------------------------
$zIndex-1:   100;
$zIndex-2:   200;
$zIndex-3:   300;
$zIndex-4:   400;
$zIndex-5:   500;
$zIndex-6:   600;
$zIndex-7:   700;
$zIndex-8:   800;
$zIndex-9:   900;
$zIndex-10: 1000; // level 10 reserved for debuging and tools


// Z-Index Applications (module based)
// syntax :
// $zIndex-level--componentName[__elementName[--modifierName]|[--modifierName]]: 
//   $levelVar + aTuningNumber;
// --------------------------------------------------
// Examples :
$zIndex-1--header:                          $zIndex-1 + 6;
$zIndex-1--nav__dropDown:                   $zIndex-1 + 5;
$zIndex-1--nav__nav:                        $zIndex-1 + 6;
$zIndex-1--homeIntro__container:            $zIndex-1;
$zIndex-1--highlightedCompany__gradient:    $zIndex-1 + 1;
$zIndex-1--highlightedCompany__darkLayer:   $zIndex-1 + 2;
$zIndex-1--highlightedCompany__banner:      $zIndex-1;
$zIndex-1--highlightedCompany__meta:        $zIndex-1 + 3;
$zIndex-1--instantFeedback:                 $zIndex-1 + 4;
$zIndex-1--flashMessage:                    $zIndex-1;
$zIndex-1--secondaryHeader__fakeBackLayer:  $zIndex-1 + 1;
$zIndex-1--secondaryHeader__container:      $zIndex-1;
$zIndex-1--box__inactiveModal:              $zIndex-1 + 50;
$zIndex-1--box__inactiveOverlay:            $zIndex-1 + 45;
$zIndex-1--header__branding:                $zIndex-1;
$zIndex-1--companyHeader__logoLink:         $zIndex-1 + 4;
$zIndex-1--searchBox__clear:                $zIndex-1 + 1;

$zIndex-2--mobileView:                      $zIndex-2;
                                            
$zIndex-5--moveUp:                          $zIndex-5;
                                            
$zIndex-9--stickyCta:                        $zIndex-9;
$zIndex-9--modal:                            $zIndex-9 + 1;
                                            
$zIndex-10--breakPointsViewer:              $zIndex-10;

```

## Typography
Typography has a primary role in good web design, Typography can make or break a design. being in
control of typography is a key point, defining scale variables for typography properties like font-size
font-weight, line-height, letter spacing and font-family can help a lot in maintaining and retuning typography.

Always limit number of fonts to maximum of two font faces, usually a sans type face and a sans-serif,
sometimes you may need a mono-space type for numeric counters or tables, code snippets and thing
like that.
 
You may need to have more control on some specific properties like font-size and font-weight and font-style by defining
mixins. Check font-weight mixin on [medium example](https://medium.com/@fat/mediums-css-is-actually-pretty-fucking-good-b8e2a6c78b06)
 
You should always use typography scale variables/mixins to assign to typography properties. 

```scss
// font-familly variables example
$fontFamily-sansSerif:  "Iran Sans Web";
$fontFamily-serif:  "Iran Sans Web"; // we haven't serif at all!

// font-size scale variables example
$fontSize-base:          14px; // body
$fontSize-large:         18px;
$fontSize-small:         12px;
$fontSize-tiny:          11px;
$fontSize-jumbo:         50px;

$fontSize-h1:            36px;
$fontSize-h2:            30px;
$fontSize-h3:            24px;
$fontSize-h4:            18px;
$fontSize-h5:            14px;
$fontSize-h6:            12px;

// font-weight scale variables
$fontWeight-ultralight: 200;
$fontWeight-light: 300;
$fontWeight-normal: 400;
$fontWeight-medium: 500;
$fontWeight-bold: 700;
```

```less
// line-height and letter-spacing scale variables nameing example from medium 
// https://medium.com/@fat/mediums-css-is-actually-pretty-fucking-good-b8e2a6c78b06
@lineHeight-tightest
@lineHeight-tighter
@lineHeight-tight
@lineHeight-baseSans
@lineHeight-base
@lineHeight-loose
@lineHeight-looser

@letterSpacing-tightest
@letterSpacing-tighter
@letterSpacing-tight
@letterSpacing-normal
@letterSpacing-loose
@letterSpacing-looser
```
