
# Sanam Style Convention

**Sanam, A minimal and flexible approach to developing maintainable & large scalable stylesheet.**

Sanam is a Style Convection based on some of the best practices, methods, articles
and current style guides. Sanam goal is to provide a set of conventions that lets programmers achieve following goals.

1. clean well structured and transparent code
2. highly reusable code
3. maintainability in long term and large scale
4. highly readable code via simplicity and being explicit 
5. flexibility in term of development and conventions itself
 
Sanam borrows some of it’s main Ideas and features from following resources:

- Namespaces idea from [Harry Roberts Article](http://csswizardry.com/2015/03/more-transparent-ui-code-with-namespaces/)
- BEM css syntax as component/module pattern convention [BEM](https://en.bem.info/)
- Variables and scale variables idea [Fat Article on Medium](https://medium.com/@fat/mediums-css-is-actually-pretty-fucking-good-b8e2a6c78b06)
- General idea of directory structure the 7-1 pattern [Sass Guidelines](http://sass-guidelin.es/)
- Limiting preprocessors features Based on numerous articles including[(1)](http://csswizardry.com/2012/05/keep-your-css-selectors-short/)[(2)](http://thesassway.com/intermediate/avoid-nested-selectors-for-more-modular-css)[(3)](http://www.sitepoint.com/avoid-sass-extend/)
- Some other articles from [This Repo](https://github.com/davidtheclark/scalable-css-reading-list) that I will mention later 

Sanam documentary is based on SASS-Lang, but it can be adopted to be used with conjunction
of any preprocessor language or even pure css using postprocessors or task runners.
Suggesting a collection of best practices is the goal of Sanam, Sanam Style Convention
does not provide any code or framework for specific language or any opinionated structure,
you should get the core principles and implement them in your projects as suits your situation.

# Table Of Contents
1. [About Author](#about-author)
2. Namespaces
3. Util Classes
4. layout Classes
5. Scoping Classes
6. Theme Classes
7. State Classes
8. Javascript Classes
9. Testing Classes
10. Hack Classes
11. Objects
12. Component/Modules
13. Layout Level Objects
14. Page Level Styles
15. BEM
16. Responsive
17. Variables
18. Colors
19. Color Pallet
20. Gray Shades
21. Semantic Colors
22. Z-index
23. Typography
24. Limiting preprocessors features
25. Nesting
26. Loops & Branching
27. Mixins
28. Extend
29. Vendors
30. Vendors Override
31. Legacy styles 
32. Shame styles
33. Big Picture of Directory structure
34. Documentation
35. Common Sense 

# About Author
My name is Sajjad M.Beiraghdar, I'm 30 Year old Frontend developer & UX Designer 
and former FullStack Developer From Tehran,Iran.
I'm currently working in Jobinja.ir as Co-Founder and Frontend Developer.
I began Programing since 1998 as a kid. Currently I have 5 years of professional experience,
working with professional companies and talent people. I worked on several real world enterprise projects
with ten thousand LOC of poorly maintained CSS and Javascript and everybody on the team would touch CSS regularly.
Sanam is the outcome of my effort to establish a style convention in my former company.
After reading lots of articles & methodologies I conducted this convention,
Sanam is a subset and un-opinionated version of that effort.
I used this convention on several project with major refactors and the results was like magic. 
After few weeks we had a clean, easy to read and modify large code base!
I strongly recommend Sanam Style Convention for new projects. It helps Your code keep clean 
and easy maintainable even with newcomer team members. Every body how get familiar with convention
can maintain the project stylesheet. In case of project refactoring establishing suitable workflow
is necessary, in large project with around 5K LOC or more stylesheets using a CSS test framework to
detect broken styles during refactor can help a lot.

# Namespaces
The main reason of lacking an easy to read and maintain codebase in scale is lack of clarity and
confidence, people aren’t confident what are the side effects of modifying a selector,
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
just by the class name itself right in html.

> *Namespace*: namespaces are one or more character at the beginning of class and are separated from
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

Sanam Style Convention suggests twelve different name spaces as following 

## Utility Classes (u-)
Utility classes are simple classes with a specific small task. Common examples of
this type of classes are floating, clearFix, text alignment classes. these classes are
reusable and can be used anywhere and should not be bound onto or changed, they can be added
anywhere and remove to do their small specific task without any side effect, they should not
participate in other selectors, this is the meaning of not bounding onto them.

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

## Layout Classes (l-)
Layout Classes are responsible for structure and cosmetic of a specific layout type in project,
in most project they have rare use cases. They should not be bound onto. This type of
classes uses BEM convention to name layout and it’s element. 

>BEM convention will covered in section 15

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

## Scoping Classes (s-)

---

# License
 
 (The MIT License)
 
 Copyright (c) 2014-2016 Smbeiragh
 
 Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the 'Software'), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:
 
 The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.
 
 THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
 

