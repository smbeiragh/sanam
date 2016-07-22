## Limiting preprocessors features
CSS is a simple and declarative language so every language that compiles to css should be
simple to read and write. preprocessor languages like sass, less and others goal is solving
CSS language issues.

I refer to [Hugo Giraudel](http://hugogiraudel.com/) quote on [SASS Guidlin](http://sass-guidelin.es/)
> Meanwhile, CSS is a simple language. Sass, being intended to write CSS, should not get
much more complex than regular CSS. The KISS principle (Keep It Simple Stupid) is
key here and may even take precedence over the DRY principle (Don’t Repeat Yourself)
in some circumstances.

Some features like variable and small simple functions and mixins are the most useful and harmless
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

Selector Nesting can be useful, but often can make more issues than solves.

1. it makes codebase unsearchable.
2. it makes code less easy to read.
3. it can increase potential use of descendant selector.
4. it can decrease modularity

To read more about this, check [Sass Guidlin](http://sass-guidelin.es/) and it's references on 
[these](http://www.sitepoint.com/beware-selector-nesting-sass/)
[good](http://thesassway.com/beginner/the-inception-rule)
[articles](http://thesassway.com/intermediate/avoid-nested-selectors-for-more-modular-css) 
 
We should limit selector nesting by following rules

1. limit selector nesting to a maximum level .e.g 3 or 4 levels, it's even better avoid them as
long as possible
2. limit selector nesting to pseudo-classes, pseudo-elements, state classes to keep everything
 about a component/selector in one place.
3. limit use of selector nesting and descendant selectors to necessary cases    

## Loops & Branching
Loops and conditional statement are not for everyday use. theses features are useful in complex
codes like libraries and frameworks. we should limit use of them as much as possible. keep readability
and simplicity in mind, Reading 10 selectors is much simpler than reading a loop, but writing a loop to 
generate 100 selectors is rational, although before doing this we should think why we need 100 selectors,
may be we're doing something wrong.

## Mixins
Mixins are similar to partials in templating languages. Mixins are powerful enough to take care about 
Mixins abuse. Try not to write complex mixins, keep them small and simple. over using mixins
can increase stylesheet size because every single call of a mixin is equal to repeat all the mixin code
in compiled css. Use css classes as reusable units instead of mixins when ever it is possible and
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
