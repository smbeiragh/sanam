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
1. [About Author](content/about-author.md#about-author)
2. [Namespaces](content/namespaces.md#namespaces)
3. [Utility Classes](content/namespaces.md#utility-classes-u-)
4. [Scoping Classes](content/namespaces.md#scoping-classes-s-)
5. [Theme Classes](content/namespaces.md#theme-classes-t-)
6. [State Classes](content/namespaces.md#state-classes-is-has-)
7. [Javascript Classes](content/namespaces.md#javascript-classes-js-)
8. [Testing Classes](content/namespaces.md#testing-classes-qa-)
9. [Hack Classes](content/namespaces.md#hack-classes-_)
10. [Objects](content/namespaces.md#objects-classes-o-)
11. [Components/Modules](content/namespaces.md#components-modules-classes-c-)
12. [Layouts](content/namespaces.md#layout-classes-l-)
13. [Layout Level Objects](content/namespaces.md#layout-level-objects-lo-)
14. [Page Level Styles](content/namespaces.md#page-level-styles-p-)
15. [Modular Pattern](content/modular-pattern.md#modular-pattern)
16. [Responsive](content/responsive.md#responsive)
17. [Variables](content/variables.md#variables)
18. [Colors](content/variables.md#colors)
19. [Color Pallet](content/variables.md#color-pallet)
20. [Gray Shades](content/variables.md#gray-shades)
21. [Semantic Colors](content/variables.md#semantic-colors)
22. [Brand Colors](content/variables.md#brand-colors)
22. [Z-index Scale](content/variables.md#z-index-scale)
23. [Typography](content/variables.md#typography)
24. [Limiting preprocessors features](content/limiting-preprocessors-features.md#limiting-preprocessors-features)
25. [Selector Nesting](content/limiting-preprocessors-features.md#selector-nesting)
26. [Loops & Branching](content/limiting-preprocessors-features.md#loops-branching)
27. [Mixins](content/limiting-preprocessors-features.md#mixins)
28. [Extend](content/limiting-preprocessors-features.md#extend)
29. [Vendors](content/vendors-and-etc.md#vendors)
30. [Overriding Vendors](content/vendors-and-etc.md#overriding-vendors)
31. [Legacy styles](content/vendors-and-etc.md#legacy-styles) 
32. [Shame styles](content/vendors-and-etc.md#shame-styles)
33. [Reset styles](content/vendors-and-etc.md#reset-styles)
34. [Environment variables](content/vendors-and-etc.md#environment-variables)
35. [Big Picture of Directory structure](content/big-picture.md#big-picture-of-directory-structure)
36. [Documentation](content/final.md#documentation)
37. [Common Sense](content/final.md#common-sense) 
      
# License 
[Creative Commons Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0/legalcode)