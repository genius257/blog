---
layout: post
title: My vision for AutoIt
categories: AutoIt
---

AutoIt is an interesting language. It's a interpreted language, with a small executable size and has a pretty good compatibility with older versions of windows.

But it is a language that seems stuck in it's old ways. It does very little to improve it's core experience, and as a result it is falling into obscurity.

<script type="text/javascript" src="https://ssl.gstatic.com/trends_nrtr/3975_RC01/embed_loader.js"></script>
<script type="text/javascript">
trends.embed.renderExploreWidget("TIMESERIES", {"comparisonItem":[{"keyword":"/m/070m83","geo":"","time":"2004-01-01 2025-02-01"}],"category":0,"property":""}, {"exploreQuery":"date=all&q=%2Fm%2F070m83&hl=en","guestPath":"https://trends.google.com:443/trends/embed/"});
</script>

I have a vision for the future of AutoIt, where it becomes more relevant again. Below are the things I am working towards and hope to realize one day.

## Developer experience

The AutoIt developer experience is the biggest problem with AutoIt, in my opinion.

### Editor

The official recommended editor for developing AutoIt is a modified version of SciTE, included with every installation of AutoIt.  
It works fine and have been customized, to provide some nice to have features, but seems to be less relevant than ever, with more and arguably better editor choices, making it bundled with each release more or less redundant.

There are existing solutions for popular editors, like extensions, for working with AutoIt files, and providing the same or more developer features.  
Visual studio code, for example have multiple extensions, [one of them created and maintained by me](https://marketplace.visualstudio.com/items?itemName=genius257.autoit).

### Static type checking

No type checking exists currently, but with the currently limited number of types AutoIt has, it would not be too complicated to implement a basic static type checking implementation.

This is something I plan to implement in the future, but are currently deciding if my target implementation language should be TypeScript, AutoIt or both.

### Debugging

With no official debug features available in the runtime, debugging options are limited to writing to the console, or getting the current line number being executed in a tooltip when hovering over the associated tray icon.

To introduce actual debugging to AutoIt, a runtime emulator is needed, since the source has been private since [2006](https://www.autoitscript.com/forum/topic/36379-autoit-32x-public-source-code/).  
For this issue, my goal is to write a AutoIt parser and executor, written in the AutoIt language. I expect the performance to be horrible, but it will make it easier to mimic specific runtime details of the AutoIt runtime.

### Less bloat

Downloading a AutoIt release is always as a complete developer bundle. This makes sense for development usage, but not great for CI tools, needing to download a ~16mb archive file to get a ~1mb executable file and maybe ~5mb standard included scripts containing helpful functions and variable declarations.

There is no simple good solution here, unless it involves the official AutoIt owners to change the way they provide the releases.  
A unofficial solution could be made, but this seems like a grey area.

## Language improvements

### Open source

I don't expect the AutoIt source code to be open source once again.  
But implementing a open source parser and runtime solution with as close to compatible as can be seems to be the next best thing.

For me personally I would like to imagine my parser solution slowly being able to convert parts of AutoIt code into assembly, until it finally might become it's own thing, AKA Bootstrapping.  
If this is realistic and how long it would take is something I am nowhere near of finding out, and may never be. Time will tell.

### Tray icon

AutoIt always creates a tray icon, when initially launched. For running scripts automatically this can appear glitchy and unwanted, even if removing or hiding the tray icon as the first action of the script.

I do not expect the official AutoIt solution to ever change this, so modifying the executable itself or using a compatible non official runtime seems to be the only solution, neither seems ideal.
