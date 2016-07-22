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
25. [Selector Nesting](#selector-nesting)
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
36. [Documentation](content/final.md#documentation)
37. [Common Sense](content/final.md#common-sense) 
      
# License 
[Creative Commons Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0/legalcode)