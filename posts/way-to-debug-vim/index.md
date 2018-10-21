<!--
.. title: way to debug vim
.. slug: way-to-debug-vim
.. date: 2018-10-21 21:50:28 UTC+08:00
.. tags: vim, debug
.. category: note
.. link: 
.. description: 
.. type: text
-->

Find the right issue submit info, might be some info for getting verbose of runtime debug. Such as [SpaceVim Issue Tracker](https://github.com/SpaceVim/SpaceVim/issues) or [vim-jedi issue tracker](https://github.com/davidhalter/jedi-vim/issues), providing detailed guide for stepwise debugging info

## Dis functional shortcut key

Typical scenario would be triggered some error or unexpected behavior after press some key. Then it's essential to get the details by identify what happened firstly after certain key pressed (or what vim thought should be happened)

``` vim
:verb map K?
```
## Python Plugin

For python plugin, try to find python env issue inside of vim

```python
:python import sys; print sys.path; import jedi

```

## To Be Continue
