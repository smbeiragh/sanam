
# Sanam Style Convention

**Sanam, A minimal and flexible approach to developing maintainable & large scalable stylesheet.**

Sanam is a Style Convection based on some of the best practices, methods, articles
and existing style guides. Sanam goal is to provide a set of conventions that lets
programmers achieve following goals.

1. clean well structured and transparent code
2. highly reusable code
3. maintainability in long term and large scale
4. highly readable code via simplicity and being explicit 
5. flexibility in term of development and conventions itself
 
Sanam borrows some of it’s main Ideas and features from following resources:

- Namespaces idea from [Harry Roberts Article](http://csswizardry.com/2015/03/more-transparent-ui-code-with-namespaces/)
- [BEM](https://en.bem.info/) css nameing convention as component/module pattern convention
- Variables and scale variables idea from [Fat's Article on Medium](https://medium.com/@fat/mediums-css-is-actually-pretty-fucking-good-b8e2a6c78b06)
- General idea of directory structure & the (n-1)7-1 pattern from [Sass Guidelines](http://sass-guidelin.es/)
- Limiting preprocessors features Based on numerous articles including [(1)](http://csswizardry.com/2012/05/keep-your-css-selectors-short/)[(2)](http://thesassway.com/intermediate/avoid-nested-selectors-for-more-modular-css)[(3)](http://www.sitepoint.com/avoid-sass-extend/)
- Some other articles from [This Repo](https://github.com/davidtheclark/scalable-css-reading-list) that I will mention. 

Sanam documentary is based on SASS-Lang, but it can be adopted to be used with conjunction
of any preprocessor language or may be pure css using postprocessors or task runners.
Suggesting a collection of best practices is the goal of Sanam, Sanam Style Convention
does not provide any code or framework for specific language or any opinionated structure,
you should get the core principles and implement them in your projects as suits your situation.

# Table Of Contents
1. [About Author](#about-author)
2. [Namespaces](#namespaces)
3. [Utility Classes](#utility-classes-u-)
4. [Scoping Classes](#scoping-classes-s-)
5. [Theme Classes](#theme-classes-t-)
6. [State Classes](#state-classes-is-has-)
7. [Javascript Classes](#javascript-classes-js-)
8. [Testing Classes](#testing-classes-qa-)
9. [Hack Classes](#hack-classes-_)
10. [Objects](#objects-classes-o-)
11. [Components/Modules](#components-modules-classes-c-)
12. [Layouts](#layout-classes-l-)
13. [Layout Level Objects](#layout-level-objects-lo-)
14. [Page Level Styles](#page-level-styles-p-)
15. [Modular Pattern](#modular-pattern)
16. [Responsive](#responsive)
17. [Variables](#variables)
18. [Colors](#colors)
19. [Color Pallet](#color-pallet)
20. [Gray Shades](#gray-shades)
21. [Semantic Colors](#semantic-colors)
22. [Brand Colors](#brand-colors)
22. [Z-index Scale](#z-index-scale)
23. [Typography](#typography)
24. [Limiting preprocessors features](#limiting-preprocessors-features)
25. [Selector Nesting](#sselector-nesting)
26. [Loops & Branching](#loops-branching)
27. [Mixins](#mixins)
28. [Extend](#extend)
29. [Vendors](#vendors)
30. [Overriding Vendors](#overriding-vendors)
31. [Legacy styles](#legacy-styles) 
32. [Shame styles](#shame-styles)
33. [Reset styles](#reset-styles)
34. [Environment variables](#environment-variables)
35. [Big Picture of Directory structure](#big-picture-of-directory-structure)
36. [Documentation](#documentation)
37. [Common Sense](#common-sense) 

# About Author
My name is Sajjad M.Beiraghdar, I'm 29 Year old Front-end developer & UX Designer 
and former Full Stack Developer From Tehran,Iran.
I'm currently working in Jobinja.ir as UX Designer and Front-end Developer.
I began Programming since 1998 as a kid. I begun my professional carer since 2011,
working with professional companies and talent people. I worked on several real world enterprise projects
with ten thousand LOC of poorly maintained CSS and JavaScript and everybody on the team would touch CSS regularly.
Sanam is the outcome of my effort to establish a style convention in my former company.
After reading lots of articles & methodologies I conducted this convention,
Sanam is a subset and un-opinionated version of that effort.
I used this convention on several project with major refactor and the results was like magic. 
After few weeks we had a clean, easy to read and modify large code base!
I strongly recommend Sanam Style Convention for new projects. It helps you to keep your code clean 
and easy to maintain and modify even with newcomer team members. Every body how get familiar with convention
can maintain the project stylesheet. In case of project refactoring establishing suitable workflow
is necessary, in large project with around 5K LOC or more stylesheets using a CSS test framework to
detect broken styles during refactor can help a lot.

# Namespaces
The main reason of lacking an easy to read and maintain codebase in scale is lack of clarity and
confidence, people arn’t confident what are the side effects of modifying a css rule,
what does a selector and what are it’s use cases as a result we afraid to touch old codes so we start to
avoid touching them and adding new selectors for every change, soon it will end up to more and
more selectors that nobody knows what each one does. So we have to spend most of our time on reading old 
code instead of developing.
  
As Harry Roberts said in his [article](http://csswizardry.com/2015/03/more-transparent-ui-code-with-namespaces):
>“We need to say exactly what a class does, why it exists, where (else) it might already occur,
> whether or not we can reuse it elsewhere, and how safe it is to bind onto or modify.”
  
So should we provide lengthy documentation on every single class and selector?
A good code is a self documentary code. Meaningful classes are the the answer.
By using namespaces we’re able to communicate useful information about classes to other developers
just by the class name itself right in html or css code.

> *Namespace*: namespaces are one or more character at the beginning of class name and are separated from
> other parts of class names using hyphen (-) 

*Example of Namespace*
```css
.u-pullLeft{
    float: left;
}
```

the above example shows a utility class called ‘pullLeft’, and it’s a utility class because it
begins with ‘u’ namespace and this telling us several useful information.

1. this is a utility class
2. we should not edit it  
3. it is doing on single task and that is floating left
4. this can be reused anywhere to float left anything
5. we should not bind on it, for example writing a selector like ‘.some-class .u-pullLeft’

Sanam Style Convention suggests twelve different name spaces as following. You can adopt your own set of
name spaces to fit your work, keeping in mind 1)each namespace should have a specific and simple to understand goal
and 2)keep numbers of namespaces small as small possible   

## Utility Classes (u-)
Utility classes are simple classes with a specific small task. Common examples of
this type of classes are floating, clearFix, text alignment classes. these classes are
reusable and can be used anywhere and should not be bound onto or changed, they can be added
anywhere and remove to do their small specific task *without any side effect*, they should not
participate in other selectors, this is the meaning of not bounding on to them.

Utility classes name space is **u-** 

```css
/* GOOD */
.u-pullLeft{
    float: left;
}

/* BAD */
.someClass .u-pullLeft{
    color: blue;
}
```

## Scoping Classes (s-)
Scoping classes lets to define a scope of DOM whit special styles, .e.g in content manage management
system, dynamic contents like post and pages can be considered as content scope, under content scope
we can setup a custom typography, styling headings, paragraphs etc.
These classes can lead to pure css codes and should be used wisely and limited. 

```css
/* the p tag style in cms content scope */
.s-cmsContent p{
 margin-bottom: 1rem
}
```

## Theme Classes (t-)
Template classes like Scoping classes are a mean to define a scope of DOM, in this case for
cosmetic changes. This type of class used typically in style switchers.

``` css
/* the main header of page in sky theme */
.t-skyThem c-mainHeader{
 background-color: blue;
}
```
 
## State Classes (is-, has-)
State classes define a piece of UI in a temporary specified state or condition,
e.g. is-hidden, is-selected, is-disabled, .etc  
As Harry Roberts says:
>It tells us that the DOM currently has a temporary, optional, or short-lived style applied to it due to a certain state being invoked.

``` css
/* the main header in collapsed state */
.c-mainHeader.is-collapsed{
 background-color: blue;
}
```
 
## Javascript Classes (js-)
These classes are javascript hooks to DOM. Styles should not be bound onto these classes,
they tell developer this class is a javascript hook and should not be removed or changed
or bound on to or rely on them. 

## Javascript Classes (qa-)
These classes like js classes are hooks to DOM for test tools. Like js classes shouldn't 
be bound on to or apply styles on them.

## Hack Classes (_)
These classes are the worst classes, they're quick fixes and hacks. sometimes we need to
apply a class on DOM to force something to work.
We need to tell this class is less than ideal and temporary.

Example:
```html
<!-- force an icon to move to right side by one pixel -->
<i class="c-icon c-icon--close _goRight">
</i>
```

Example:
```css
_goRight {
    position: relative;
    left:1px;
}
```  

## Objects Classes (o-)
Object classes are abstracted pure structural and none cosmetic reusable piece of UI.
they may be used anywhere and modifying them may have undesired side effects on many
other unknown places. generally we should avoid modifying them or be careful about 
modifying them. Objects considered to follow open/closed principle, it means they are open 
to extending but close to modifying. We often extend them and only modify them on major refactor.
Sanam recommends use of BEM methodology on this namespace.
  
>BEM convention will covered in section 15  

Format:
``` css
.o-objectName[<element>|<modifier>] {}
```

Examples:
``` css
// widget object root element class
.o-widget {}

// widget heading element class
.o-widget__heading {}
```

## Components/Modules Classes (c-)
Components are reusable piece of UI.They can represent any visual repetitive piece of UI that anyone can
recognize them. Like buttons, dropdowns and so on. A component may have other components as children
(composition) but a component may not extend other components but may extend an *Object*. By this limitation
on extending, we limit modifying side effects to modified component, it lets us to confidently
edit that component and check all instances of that component with a simple search while finding all instance of
several unknown components that are extending a modified component needs careful checking in markup and it can
be a large amount of effort. In contrast to Objects, components are close to extending but open to modifying.
like objects, component classes benefits BEM methodology.

>BEM convention will covered in section 15  
  
Format:
```css
.c-componentName[<element>|<modifier>] {}
```

Examples:
```css
// navbar components root element class
.o-navbar {}

// navbar logo element class
.o-navbar__logo {}
```  

## Layout Classes (l-)
Layout Classes are responsible for structure and cosmetic of a specific layout type in project,
in most projects they have rare use cases. They should not be bound onto. Layout classes 
benefits BEM methodology.

```css
/* the default layout root element */
.l-default{
    background-color: #f9f9f9;
}

/* the default layout sidebar element */
.l-default__sidebar{
    background-color: #f5f5f5;
}

/* BAD */
/* You are not supposed to bound on layout class */
.l-default__sidebar .someClass{
    color: blue;
}
```

## Layout Level Objects (lo-)
Sometimes there are few shared common features in between different layouts, like fixed footer.
layout level objects are a mean to make this type of features reusable and encapsulated in a 
set of classes. Like layout classes, layout level object benefits BEM methodology 

## Page Level Styles (p-)
Sometimes we need to apply style on specific page. In well designed component based
system this can happen rarely. Sanam suggests to provide a top level scoping class
.e.g on body or html tag using a name based on page name. under this scope we can
override every aspect of page including components and layout. but keep in mind modifying a
component or layout in page level can be a sign of lacking a modifier on component
level or layout level and writing page level style generally is not a good idea and
can be lead to hard to maintain code. 
When modifying any thing, try to be explicit and don't bound on classes of different
namespaces by defining classes in page level namespace.

```css
// the root class on body tag for scoping
.p-home {
}

// root element of navbar component of home page
.p-home__nav {
}

// item elemet of navebar component on home page
.p-home__nav__item{
}

// BAD, bounding on component class
// this can overide all nav components on home page
.p-home .c-nav__item{
}
```

## Modular Pattern
Modularity lets us to organize most of our code in small reusable and
easy to understand and maintain pieces. Modularity in software brings
many benefit including encapsulation, extensibility and compositions.
using this pattern we bring the same benefits in CSS.

*encapsulation*: 
every module handles all of it's aspects including it's own state, elements, modifiers and
has noting to with other modules.

1. Every module defines its own style in a separate file
2. A module file contains only and only styles related to one module
3. Every module has a root element which contains all elements of that module   
4. CSS selectors of a module only includes classes of that module
5. Every module can be used every where independent of it's own and document DOM Structure.   
6. A child module should not know anything about it's parent module
7. A parent module should not know anything about child module
 
*extensibility*: 
A module can extend from objects, To keep maintenance simple Sanam limits extending to objects.
When two modules has same element as root element we say one is extending another. this can
be considered as special case of compositions where parent and child are at the same level.

1. Components (modules in C namespace) can only and only extend Objects (modules in O namespace)
2. Modules can modify base component elements/modifiers via its own module classes and not base
module classes

```html
<!-- c-usersList extending o-list -->
<ul class="c-usersList o-list">
    <!-- c-usersList can modify o-list__item(item element) via c-usersList__item -->
    <li class="c-usersList__item o-list__item"></li>
</ul>
```

*compositions*: 
A module can contain another module(s) as children.

1. A parent module should not know about child module, and should not modify child component.
2. A parent module can modify child component root element as its own element via parent module classes and 
not child module class

```html
<!-- c-actionBar composed of bottons and c-userList -->
<div class="c-actionBar">
    <input class="c-btn c-btn--primary c-actionBar__action">
    <input class="c-btn c-btn--default">
    <input class="c-btn c-btn--default">
    <ul class="c-usersList o-list c-actionBar__list">
        <!-- c-usersList can modify o-list__item(item element) via c-usersList__item -->
        <li class="c-usersList__item o-list__item"></li>
    </ul>
</div>
```
In this example c-actionBar can modify child bottom via c-actionBar__action,
action element my be anything and c-actionBar just know there is a
number or action elements an noting more, similarly c-actionBar can modify c-usersList root element
via c-actionBar__list, but it shouldn't modify c-userList items, because actionBar dose't know anything
about c-usersList internals or event about its existence! if we would like to modify list it should be
done as modifier on c-userList or o-list to unify all lists in project level not based on parent
component of list.

There are several modular conventions including BEM, OCSS, SMACSS, DRY CSS. 
Sanam recommends [BEM](https://en.bem.info/) as modular convention in several
namespaces including Components (c-), Objects (o-), Layouts (l-), Layout Objects (lo-)
and Page level (p-)

### Block-Element-Modifier (BEM)
[BEM](https://en.bem.info/) is a modular convention from Russian search engine Yandex.
BEM is similar to OOP and lets us to use OOP concepts in CSS. 

BEM has three main parts:

**Blocks**:
Blocks are reusable and independent units of code, also called modules, 
components and widgets. Every UI is composed of Blocks

**Elements**:
Every block or module consists of Element, for example a figure consists of caption and image element.

**Modifiers**:
Modifiers are a mean to define permanent or temporary state of a module or its module elements.

BEM define a naming convention for class names as following 

```css
// syntax
.blockName[__elementName][--modiferName]

// syntax with namespaces
.nameSpace-blockName[__elementName][--modiferName]
```
  
```css
// the navbar block root element
.c-nav{}

// the link element in navbar
.c-nav__link{}

// the logo element in navbar block
.c-nav__logo{}

// the logo element in navbar block and the logo is in small mode
.c-nav__logo--small{
}
```

```html
<nav class="c-nav">
    <a class="c-nav__link" href="#"></a>
    <img class="c-nav__logo c-nav__logo--small"> 
</nav>
```

Following principles applies to BEM

1. Every block must have a unique name
2. Every block can contains several elements with unique names
 in scope of tha block
3. Every block can contains several elements with the same name
4. Tag names should not be used in css selectors 
5. Descendant selectors should be avoided except when applying
 a top level modifier or state class.
  
> Sanam uses camelCase naming and (-, --, __) as semantic seperators   
 
Read More about BEM in practice in these [great](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/) [articles](https://css-tricks.com/bem-101/) and [website](http://getbem.com/)  

## Responsive
Developing responsive website using pure media queries is not scalable even in website with few pages.

1. using pure media queries is not scalable
2. final code is not readable enough
3. designers and developers communication is not easy
4. changing a breakpoint is painful

To address this issues, Saname recommends use of named breakpoints and an API e.g. a mixin via a pre-processor
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

## Variables
Sanam Uses Following syntax for defining variables. all following parts are camelCase

```css
<propertyName>-<valueName>[--componentName[__elementName[--modifierName]]]
```

This syntax has several benefits:

1. great auto complete by IDE, for example when you are going to set a color
 by typing color IDE will show a list of all color variable
2. property name and value name give us a good idea about what this variable
 contains
3. component naming part tells where this variable is used if bounded to a component. 

## Colors
Sanam Organize colors in four different categories including pallet colors, 
gray scale colors, semantic colors and brand colors. Colors are one of types
that can go out of control easily, managing number of colors can help reduce
styles size. To mange colors applying all colors must be done via variables,
also using an API like a SASS function can be useful but simplicity in this
area can be more useful. Sanam suggests simple variables because:

1. variables are easier to locate and search
2. variables lets us benefit IDE auto complete

hsl(hue, saturation, lightness) color format is recommended because:

1. it's more understandable and meaningful to humans
2. it's easier to notice un-intended color changes

sometimes we need to create an extra shade of a defined color which is not pre
defined in variable in such cases we can use helper function to apply a custom
shade or alpha chanel, but this cases should be minor. if it often happens it 
may you should re-tune predefined shades or add a few more shades as predefined
and don't let number of colors go out of control.

## Pallet Colors
Base on colors theory there are four type color pallets.

1. *Mono color* with a single primary color
2. *Adjacent colors* and *Triad colors* with one primary color and two secondary colors)
3. *Tetrad* colors with four colors one primary color and two secondary colors plus
 a complement color

Sanam define four different color name as primary, secondary1, secondary2 and a 
complement for the maximum number of colors and semantic names for several shades
of each color. base on variable naming convention an example can look like this

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
picky about color specially about gray shades. they would like to tune them
test them and so on. this can very easily end to having lots of gray shades
in small project. it's enough to have five or seven gray shades like pallet colors
but if you think that's not working for you, Sanam recommends useing variable names
with color code in their name. By doing this next time we try to apply a new gray
shade IDE will show us list of all defined shades and we can chose to add 
a new shade or pike one of predefined shades. In case of not using IDE,
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
Z-index values can go out of control very easily. Even in small projects z-index headache is common.
Setting arbitrary numbers on z-index and inspecting everything to make sure everything is working
is'nt scalable even on small projects. Defining all z-index values in a single file can help us to
keep an eye on all layers and their situation relative to each other. 
based on [this article](https://medium.com/@fat/mediums-css-is-actually-pretty-fucking-good-b8e2a6c78b06#.c6i9flixv)
every z-index value should be defined in z-index file using following syntax:

```scss
$zIndex-level--componentName[__elementName[--modifierName]|[--modifierName]]
```
   
Level is a number between 1 and 10 that refers to teen private levels of z-index. they are private
variables in z-index scale file and should't be use directly out side of that file.

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
 
You may need to have more control on some specefic properties like font-size and font-weight and font-style by defining
mixins. Check font-weight mixin [example](https://medium.com/@fat/mediums-css-is-actually-pretty-fucking-good-b8e2a6c78b06)
 
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
$fontSize-jombo:         50px;

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

## Limiting preprocessors features
CSS is a simple and declarative language so every language that compiles to css should be
simple to read and write. preprocessor languages like sass, less and others goal is solving
CSS language issues.

I refer to [Hugo Giraudel](http://hugogiraudel.com/) quote on [SASS Guidlin](http://sass-guidelin.es/)
> Meanwhile, CSS is a simple language. Sass, being intended to write CSS, should not get
much more complex than regular CSS. The KISS principle (Keep It Simple Stupid) is
key here and may even take precedence over the DRY principle (Don’t Repeat Yourself)
in some circumstances.

Some features like variable and small simple functions are the most useful and harmless
features of preprocessors. Other should be used carefully.   

## Selector Nesting
Selector Nesting is one of the most popular features of preprocessors. Selector Nesting lets
us to write a selector inside another.

```scss
.foo{
    .bar{
    }
}
```
compiles to:
```css
.foo .bar{}
```

Selector Nesting can be useful, but often can make more issus than solves.

1. it makes codebase unsearchable
2. it makes code less easy to read
3. it can increase use of descendant selector and decrease modularity

To read more about this, check [Sass Guidlin](http://sass-guidelin.es/) and it's references on 
[these](http://www.sitepoint.com/beware-selector-nesting-sass/)
[good](http://thesassway.com/beginner/the-inception-rule)
[articles](http://thesassway.com/intermediate/avoid-nested-selectors-for-more-modular-css) 
 
We should limit selector nesting by following rules

1. limit selector nesting to a maximum level .e.g 3 or 4 levels
2. limit selector nesting to pseudo-classes, pseudo-elements, state classes to keep everything
 about a component/selector in one place
3. limit use of selector nesting and descendant selectors to necessary cases    

## Loops & Branching
Loops and conditional statement are not for everyday use. theses features are useful in complex
codes like libraries and framework. we should limit use of them as much as possible. keep readability
and simplicity in mind, Reading 10 selectors is much simpler than reading a loop, but writing a loop to 
generate 100 selectors is rational, although before doing this we should think why we need 100 selectors
may be we're doing something wrong.

## Mixins
Mixins are similar to partials in templating languages. Mixins are powerful enough to take care about 
Mixins abuse. Try not to write complex mixins, keep them small and simple. over using mixins
can increase stylesheet size because every single call of a mixin is equal to repeat all the mixin code
in compiled css. Use css classes as reusable units instead of mixins when ever is it possible and
reasonable for you, it's not about zero or one, you should keep a balance and choose when use mixins vs
classes

## Extend
Extending in preprocessors is a powerful feature an very promising, but also has many problems.

Sanam strongly recommends to avoid using extend, it has more pain than gain.

1. Extending is not easy to read and understand, extending is invisible as Hugo Giraudel 
 [explains](http://www.sitepoint.com/avoid-sass-extend/).
2. Extending output is not so predictable in teamwork or when extending from libraries and frameworks 
3. Extending output is less readable
4. Extending can result in unusual large selectors
5. Extending doesn't work across media queries
6. Extending doesn't necessarily help file weight

Hugo Giraudel explained it well on [this post](http://www.sitepoint.com/avoid-sass-extend/).

Harry Roberts on [his article](http://csswizardry.com/2014/11/when-to-use-extend-when-to-use-a-mixin/) said:
 
> If you are definitely, completely set on using @extend:

1. Please reconsider.
2. Use the placeholder hack.
3. Keep an eye on your output.

## Vendors
Most of projects uses 3rd parity libraries and framework, using a package manger to keep our dependacies
out of our source code is good idea, it can facilitate updating dependencies and prevent everybody on team
from editing dependencies source code.

## Overriding Vendors
Often we need to override vendors default styles, we should avoid editing dependencies source code.
overriding can happen using vendor configs or by applying some css rules to override vendor css rules 

## Legacy styles
Sometimes, for example in a refactoring phase, we may have some old unconventional stylesheet which intended
to be refactored and removed later. we keep this type of styles in a specific place, a file or a set of files
in a directory, when ever we have time to resume refactoring, we know where are old code and every body on team
knows these styles are matter to refactor and removal and any new code shouldn't developed based on them. 

## Shame styles
Sometimes in a force of time or other limitations we write unconventional hacky code, we keep these 
type of codes in a specific place, usually shame file to refactor them, every team member knows codes in
this file are temporarily hacks that should be fixed and should not develop new code based on them.

The difference between legacy styles and shame styles is about time, legacy styles are old styles
during a huge style refactor phase. we do not develop legacy style. they're legacy, but shame styles
are force codes that should be refactored and may happen in any time of project life time not a major refactor

## Reset styles
A group of styles that are responsible to define default styles of html document.
Most of projects and frameworks use normalize css or reset css, but always there are
some small things we should do in addition to using reset libraries so it's useful to 
consider a place like a file for reset styles.

## Environment variables
Sometimes we need different configs for development and productions environments.
for example we need to show breakpoints on development but hide it on production. it's possible
to achieve this using include path to force env variable files resolve to different versions for
different environments. But keep in mind we should use this just for tools config and our code
should be the same in all environments.

## Big Picture of Directory structure
To organize our code in a manageable code having a reasonable and predictable directory/files structure
is necessary. Sanam Suggests following structure as an example. this structure is just a recommendation
as a starting point, you should adopt it for your projects.

<pre>
/  
|-- base  
|   |-- _base.scss            // import all variables  
|   |-- _vars.scss            // unclassified variables  
|   |-+ vendors               // config variables of frameworks and libraries  
|   |   |- _framework1.scss  
|   |   |- ...  
|   |   |- _frameworkN.scss  
|   |  
|   |-- _colors.scss          // color variables  
|   |-- _breakpoints.scss     // responsive breakpoints variables  
|   |-- _typography.scss      // typography scale variables  
|   |-- _z_index.scss         // z-index variables  
|   |-+ env_prod  
|   |   |-- _env.scss         // production env variables  
|   |  
|   |-+ env_dev  
|       |-- _env.scss         // development env variables  
|  
|-+ mixins //  
|   |-+ modules  
|   |   |-- _module_1.scss    // module1 mixins  
|   |   |-- ...  
|   |   |-- _module_n.scss   
|   |  
|   |-- _all.scss             // all mixins in a file or set of directories  
|  
|-+ utills  
|   |-- _display.scss         // display utils none/block/inline .etc  
|   |-- _text.scss            // text color/alignment/size utill clasess  
|   |-- _padding.scss         // padding util classes  
|   |-- _margin.scss          // margin util classes  
|   |-- _general.scss         // other util classes .e.g vertical align  
|   |-- _all.scss             // imports all util classes  
|  
|-+ legacy                    // legacy directory/files styles  
|  
|-+ vendor_override           // a mean to override 3rd party styles
|   |-- _bootstrap_override.scss  
|  
|-+ layouts                   // layouts styles  
|   |-- _default_layout.scss  
|  
|-+ layout_object             // layout objects styles  
|   |-- _sticky_footer.scss  
|  
|-+ objects                   // objects styles  
|   |-- _object_1.scss  
|   |-- ...  
|   |-- _object_n.scss  
|  
|-+ modules                   // modules styles  
|   |-- _module_1.scss  
|   |-- ...  
|   |-- _module_n.scss  
|  
|-+ pages                     // page level styles  
|   |-- _about.scss  
|   |-- ...  
|   |-- _home.scss  
|
|-- _reset.scss               // reset styles  
|-- _typography.scss          // type face definitions  
|-- _shame.scss               // shame styles  
|-- main.scss                 // main entry point of our style. import all styles
</pre>  

## Documentation
Sanam styles are transparent enough and generally there should not be much worries about code documenting.
All we need is a bit of comments. Having a style guide as list of modules/objects and their capabilities
can help to remember what modules/objects we have out of box it also promotes reusability of existing
modules and objects.

## Common Sense     
coding itself is not a goal a it's a mean to achieve a goal which is developing projects in schedule and
budget. Sanam is just a set of best practices I have read or learned from my experiences. You can and
you should adopt it to your own needs. if You feel some parts are useless for you, you should put it aside
or it may you fell you need some other namespaces or names and naming conventions. for example you may
define t namespace as css transition and animations. feel free to develop new concepts but it's better
to test new ideas in pet projects not a production one!
        
# License 

 
 (The MIT License)
 
 Copyright (c) 2014-2016 Smbeiragh
 
 Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the 'Software'), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:
 
 The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.
 
 THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
 

