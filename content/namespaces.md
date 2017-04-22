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
A good code is a self documentary code. Meaningful classes are the answer.
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
and 2)keep numbers of namespaces as small as possible

## Utility Classes (u-)
Utility classes are simple classes with a specific small task. Common examples of
this type of classes are floating, clearFix, text alignment classes. these classes are
reusable and can be used anywhere and should not be bound onto or modified, they can be added
anywhere and remove to do their small specific task *without any side effect*, they should not
participate in other selectors, this is the meaning of not bounding on to them.

Utility classes namespace is **u-** 

```css
/* GOOD */
.u-pullLeft{
    float: left;
}

/* BAD */
/* should not bound on to utill class*/
.someClass .u-pullLeft{
    color: blue;
}
```

## Scoping Classes (s-)
Scoping classes lets to define a scope of DOM with special styles, .e.g in content manage management
systems, dynamic contents like post and pages can be considered as content scope, under content scope
we can setup a custom typography, styling headings, paragraphs etc.
These classes can lead to pure css codes and should be used wisely and limited. 

```css
/* the p tag style in cms content scope */
.s-cmsContent p {
 margin-bottom: 1rem
}
```

## Theme Classes (t-)
Template classes like Scoping classes are a mean to define a scope of DOM, in this case for
cosmetic changes. This type of class used typically in style switchers.

``` css
/* the main header of page in sky theme */
.t-skyTheme c-mainHeader {
 background-color: blue;
}
```
 
## State Classes (is-, has-)
State classes define a piece of UI in a temporary specified state or condition,
is-hidden, is-selected, is-disabled are some of most common state classes  
As Harry Roberts says:
>It tells us that the DOM currently has a temporary, optional, or short-lived style applied to it due to a certain state being invoked.

``` css
/* the main header in collapsed state */
.c-mainHeader.is-collapsed {
 height: 0;
 overflow: hidden;
}
```
 
## Javascript Classes (js-)
These classes are javascript hooks to DOM. Styles should not apply via these classes,
they tell developer this class is a javascript hook and should not be removed or changed
or bound on to or rely on them.

```html
<buttom class='c-nav__toggle js-navToggle'>
    <i class="c-icon c-icon-menu"></i>
</buttom>
```

## Testing Classes (qa-)
These classes like js classes are hooks to DOM for test tools. Like js classes, test classes
shouldn't be bound on to or apply styles on them.

```html
<form>
    <input type="text"/>
    <input type="submit" class="qa-submitSearchForm" value="search" />
</form>
```

## Hack Classes (_)
These classes are the worst classes, they're quick fixes and hacks. sometimes we need to
apply a class on DOM to force something to work.
We need to tell other team members this class is less than ideal and temporary, don't reuse
or develop base on this class, this type of class matters to change and refactor.

Example:
```html
<!-- force an icon to move to right side by one pixel -->
<!-- the main issue is the icon itself, we should fix it later -->
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
other unknown places of project. generally we should avoid modifying them or be careful about 
modifying them. Objects considered to follow open/closed principle, it means they are open 
to extending but close to modifying. We often extend them and only modify them on major refactor.

>Objects namespace is a modular namespace. Sanam recommends use of BEM methodology
 on modular name spaces. BEM convention will covered in section 15  

Format:
``` css
.o-objectName[<element>[<modifier>]|<modifier>|] {}
```

Examples:
``` css
// widget object root element class
.o-widget {}

// heading element of widget object
.o-widget__heading {}

// large modifier of widget object
.o-widget--large {}

// small modifier of heading element of widget object
.o-widget__heading--small {}
```

## Components/Modules Classes (c-)
Components are reusable piece of UI. They can represent any visual repetitive piece of UI that anyone can
recognize them. Like buttons, dropdowns and so on. A component may have other components as children
(composition) but a component may not extend other components but may extend an *Object*. By this limitation
on extending, we limit modifying side effects to a single modified component, it lets us to confidently
edit that component and in worst case we can check all instances of that component with a simple search while
finding all instance of several unknown components that are extending a modified component needs careful
checking in markup and it can be a large amount of effort. In contrast to Objects, components are close
to extending but open to modifying. like objects, component classes benefits BEM methodology.

>BEM convention will covered in section 15  
  
Format:
```css
.c-componentName[__element|--modifier] {}
```

Examples:
```css
// navbar components root element class
.c-navbar {}

// navbar logo element class
.c-navbar__logo {}
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

```html
<html class="l-default lo-fixedFooter">
    <body class="l-default_body lo-fixedFooter__body">
        <main class="lo-fixedFooter__main">
            ...
        </main>
        <footer class="l-default__footer lo-fixedFooter__footer">
            ...
        </footer>
    </body>
</html>
```

## Page Level Styles (p-)
Sometimes we need to apply style on specific page. In well designed component based
system this can happen rarely. Sanam suggests to provide a top level scoping class
.e.g on body or html tag using a name based on page name. under this scope we can
override every aspect of page including components and layout. but keep in mind modifying a
component or layout in page level can be a sign of lacking a modifier on component
level or layout level and writing page level style generally is not a good idea and
can be lead to hard to maintain code. 
When modifying anything, try to be explicit and don't bound on classes of different
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

[<- Back](../README.md)
