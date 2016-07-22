## Vendors
Most of projects uses 3rd parity libraries and framework, using a package manger to keep our dependencies
out of our source code is good idea, it can facilitate updating dependencies and prevent everybody on team
from editing dependencies source code.

## Overriding Vendors
Often we need to override vendors default styles, we should avoid editing dependencies source code.
overriding should be done using vendor configs or by applying some css rules to override vendor css rules,
We should keep this type of modifications in a special file/directory.

## Legacy styles
Sometimes, for example in a refactoring phase, we may have some old unconventional stylesheet which intended
to be refactored and removed later. We keep this type of styles in a specific place, a file or a set of files
in a directory, when ever we have time to resume refactoring, we know where are old code and every body on team
knows these styles are matter to refactor and removal and any new code shouldn't developed based on them. 

## Shame styles
Sometimes in a force of time or other limitations we write unconventional hacky code, we keep these 
type of codes in a specific place, usually shame file to refactor them, every team member knows codes in
this file are temporarily hacks that should be fixed and should not develop new code based on them.

The difference between legacy styles and shame styles is about time, legacy styles are old styles
during a huge style refactor phase. We do not develop legacy style. they're legacy, but shame styles
are force codes that should be refactored and may happen in any time of project life time not a 
major refactor and we may sometimes develop shame code! 

## Reset styles
A group of styles that are responsible to define default styles of html document.
Most of projects and frameworks use normalize css or reset css, but always there are
some small things we should do in addition to using reset libraries so it's useful to 
consider a place like a file for reset styles.

## Environment variables
Sometimes we need different configs for development and productions environments.
for example we need to show breakpoints on development but hide it on production. it's possible
to achieve this using include path to force env variables files resolve to different versions for
different environments. But keep in mind we should use this just for tools config and our code
should be the same in all environments.

[<- Back](../README.md)
