+++
title = "5 NeoVim Plugins I Can't Live Without"
date = "2023-09-06T01:28:54+08:00"
author = "Tyler"
cover = ""
tags = ["neovim", "software"]
categories = ["tech"]
description = "require('very-nvim-noob').setup()"
showFullContent = false
readingTime = true
draft = false
ToC = true
ToCTitle = "Table of Content"
+++

About six months ago, [Léana](https://earth2077.fr) made me switch from JetBrains IDEs to NeoVim. As one may expect, it wasn't an easy transition from a full-blown IDE to a highly customizable text editor. It took me a long time to get used to working in a NeoVim environment (and configure it to my liking as well), but once you get the hang of it - it's just like you gained 100 XPs in a coding game!

---

## which-key.nvim

[GitHub](https://github.com/folke/which-key.nvim) | [My config](https://github.com/nottyl/dotfiles/blob/master/.config/nvim/after/plugin/which-key.lua)

{{< image src="img/which_key.png" >}}

For anyone that just started using NeoVim, one thing that'll confuse them the most is the keymaps and hotkeys of NeoVim. This plugin is here to save the day. It's basically written to help you view the keymap you've configured on the fly. Which still helps me a lot even now. (Léana sometimes still reprimand me for switching back to mouse whenever I forget the keyboard shortcuts, lol.)

---

## undotree

[GitHub](https://github.com/mbbill/undotree) | [My config](https://github.com/nottyl/dotfiles/blob/master/.config/nvim/after/plugin/undotree.lua)

{{< image src="img/undotree.png" >}}

Tired of hitting `git reset --hard` every single time you mess things up? Undotree is exactly what you need.

> *PSA: Don't be like me and use that ~~forbidden~~ command every single time :(*

Undotree shows the file history in a tree view and makes mess-ups less painful. It allows you to go back to an earlier version of the file even when it is already overwritten by the new versions of the file. Essentially, it is undo/redo function in most IDEs on steroid. While most editors only have the undo/redo function in a single session, undotree can store the entire history of your file. So cool, right?

---

## auto-save.nvim

[GitHub](https://github.com/pocco81/auto-save.nvim) | No config needed

{{< image src="img/auto-save.png" >}}

One thing that I probably will never get used to is how you need to do `:w` to write a file in NeoVim. This can quickly become a hassle if you're editing multiple files in a project and did `:w` instead of `:wa`, some of the files won't work, and it'll be a disaster.

This is probably a preference thing... but I love how most IDEs auto-save your files. Therefore, auto-save.nvim is a plugin that I simply can never live without. Once you exit insert mode, the plugin will automatically save the file for you.

---

## nvim-colorizer

[GitHub](https://github.com/norcalli/nvim-colorizer.lua) | [My config](https://github.com/nottyl/dotfiles/blob/master/.config/nvim/after/plugin/colorizer.lua)

{{< image src="img/colorizer.png" >}}

This is a very niche plugin, but it's incredibly useful in some cases. For me, it has made editing a colorscheme very easy, and it has helped me configure my old website's colorscheme. The original plugin isn't being maintained anymore, so if anyone wants to use it, please try [NvChad's fork](https://github.com/NvChad/nvim-colorizer.lua)!!

---

## gitignore.nvim

[GitHub](https://github.com/wintermute-cell/gitignore.nvim) | No config needed

{{< image src="img/gitignore.png" >}}

This plugin allows you to generate a .gitignore file in seconds, just by choosing different categories that you want to have ignored. For example, the infamous .DS_Store file in macOS, just select macOS in your gitignore.nvim and it'll generate .gitignore file for that. With this, I no longer need to type out every single file across different categories that I want to exclude from git. It is honestly a life-saver.

---

# Leave a comment!
{{< chat cactus-comments >}}
