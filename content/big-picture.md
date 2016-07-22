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

[<- Back](../README.md)
