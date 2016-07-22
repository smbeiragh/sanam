## Modular Pattern
Modularity lets us to organize most of our code in small reusable and
easy to understand and maintain pieces. Modularity in software brings
many benefit including encapsulation, extensibility and compositions.
using this pattern we bring the same benefits in CSS.

*encapsulation*: 
every module handles all of it's aspects including it's own states, elements, modifiers and
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

1. Components (modules in c namespace) can only and only extend Objects (modules in o namespace)
2. Modules can modify base component elements/modifiers via its own module classes and not base
module classes

```html
<!-- c-usersList extending o-list -->
<ul class="c-usersList o-list">
    <!-- 
        c-usersList can modify o-list__item(item element) via c-usersList__item class
        not o-list__item
     -->
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
    <!-- c-actionBar can midify btns via c-actionBar__action class
    <input class="c-btn c-btn--primary c-actionBar__action">
    <input class="c-btn c-btn--default c-actionBar__action">
    <input class="c-btn c-btn--default c-actionBar__action">
    <!-- 
        c-actionBar can midify c-usersList root element via c-actionBar__list class
        but it should not modify c-usersList enternal (elements and modifiers)
    -->    
    <ul class="c-usersList o-list c-actionBar__list">
        <!-- c-usersList can modify o-list__item(item element) via c-usersList__item -->
        <li class="c-usersList__item o-list__item"></li>
    </ul>
</div>
```

In this example c-actionBar can modify child bottom via c-actionBar__action,
action element (c-actionBar__action) my be anything and c-actionBar just know there is a
number or action elements an noting more, similarly c-actionBar can modify c-usersList root element
via c-actionBar__list, but it shouldn't modify c-userList items, because actionBar dose't know anything
about c-usersList internals or even about its existence! if we would like to modify list it should be
done via modifier on c-userList or o-list to unify all lists in project level not based on parent
component of list.

There are several modular conventions including BEM, OCSS, SMACSS. 
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
Modifiers are a mean to define variations of a module via small modification on module elements or module itself.

BEM define a naming convention for class names as following 

```css
// syntax
.blockName[__elementName[--modiferName]][--modiferName]

// syntax with namespaces
.nameSpace-blockName[__elementName[--modiferName]][--modiferName]
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
 in scope of that block
3. Every block can contains several elements with the same name
4. Tag names should not be used in css selectors 
5. Descendant selectors should be avoided except when applying
 a top level modifier or state class.
  
> Sanam uses camelCase naming and (-, --, __) as semantic separator  
 
[Read more](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/) about BEM in practice in these [great article form css wizardry](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/) [and css-tricks](https://css-tricks.com/bem-101/) and [BEM website](http://getbem.com/)  

[<- Back](../README.md)
