---
title: Neovim Noob and His Plugins
cascade:
    type: blog
date: 2023-09-06T14:17:51+08:00
tags:
- software
- neovim
categories:
- coding
authors:
- name: Tyler
description: Five neovim plugins I can't live without.
draft: false
---

About six months ago, [Léana](https://earth2077.fr) made me switch from JetBrains IDEs to Neovim. As one may expect, it wasn't an easy transition from a full-blown IDE to a highly customizable text editor. It took me a long time to get used to working in the Neovim environment (and configure it to my liking as well), but once you get the hang of it - it's like walking on air. By using a wide range of keyboard shortcuts and the clever community plugins - it'll increase your productivity by tenfold.


## which-key.nvim

[GitHub](https://github.com/folke/which-key.nvim) | [My config](https://github.com/nottyl/dotfiles/blob/master/.config/nvim/after/plugin/which-key.lua)


For anyone that just started using Neovim, one thing that'll confuse them the most is the keymaps and hotkeys of Neovim. This plugin is here to save the day. It's basically written to help you view the keymap you've configured on the fly. Which still helps me a lot even now.


## undotree

[GitHub](https://github.com/mbbill/undotree) | [My config](https://github.com/nottyl/dotfiles/blob/master/.config/nvim/after/plugin/undotree.lua)


Tired of hitting `git reset --hard` every single time you mess things up? Undotree is exactly what you need.

> *PSA: Don't be like me and use that ~~forbidden~~ command every single time, it's risky.*

Undotree shows the file history in a tree view and makes mess-ups less painful. It allows you to go back to an earlier version of the file even when it is already overwritten by the new versions of the file. Essentially, it is undo/redo function in most IDEs on steroid. While most editors only have the undo/redo function in a single session, undotree can store the entire history of your file. Dope, right?



## auto-save.nvim

[GitHub](https://github.com/pocco81/auto-save.nvim) | No config needed


One thing that I probably will never get used to is how you need to do `:w` to write a file in NeoVim. This can quickly become a hassle if you're editing multiple files in a project and did `:w` instead of `:wa`, some of the files won't work, and it'll be a disaster.

This is probably a preference thing, but I love how most IDEs auto-save your files. Therefore, auto-save.nvim is a plugin that I simply can never live without. Once you exit insert mode, the plugin will automatically save the file for you.



## nvim-colorizer

[GitHub](https://github.com/norcalli/nvim-colorizer.lua) | [My config](https://github.com/nottyl/dotfiles/blob/master/.config/nvim/after/plugin/colorizer.lua)


This is a very niche plugin, but it's incredibly useful in some cases. For me, it has made editing a colorscheme very easy, and it has helped me configure my old website's colorscheme. The original plugin isn't being maintained anymore, so if anyone wants to use it, please use [NvChad's fork](https://github.com/NvChad/nvim-colorizer.lua).



## gitignore.nvim

[GitHub](https://github.com/wintermute-cell/gitignore.nvim) | No config needed



This plugin allows you to generate a .gitignore file in seconds, just by choosing different categories that you want to have ignored. For example, the infamous .DS_Store file in macOS, just select macOS in your gitignore.nvim and it'll generate .gitignore file for that. With this, I no longer need to type out every single file across different categories that I want to exclude from git. It is honestly a life-saver.

## Leave a comment!

{{< chat 20230906001 >}}
