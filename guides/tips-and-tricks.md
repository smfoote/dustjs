---
title: DustJS | Getting Started
layout: guides
permalink: /guides/tips-and-tricks/
---

# Tips and Tricks


### Design Philosophy
Don't put business logic in your template, even if it's possible.

### Resources
* There are a set of basic <a href="https://github.com/linkedin/dustjs-helpers" target="_blank">core helpers</a> available to include in your project.  These are generally for basic logic like checking if two values are equivalent and other types of comparisons (greater than, less than).
* You can run this <a href="https://github.com/smfoote/Swiffer.js" target="_blank">Dust linter</a> to get warned while you are writing templates about possible security holes, parse errors, coding style guidelines, etc.

### Debugging
Debugging can be turned on by setting `dust.debugLevel` to one of 4 values: `"DEBUG", "INFO", "WARN", "ERROR"` before your render/renderSource/stream calls.  `"DEBUG"` will not filter out any log messages, while every level above will filter out logs below them in severity.  It is useful to set `dust.debugLevel` to `"DEBUG"` in your testing environment, and either to `"ERROR"` or unset in your production environment.