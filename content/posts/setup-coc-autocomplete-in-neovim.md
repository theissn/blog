---
title: "Setup Coc Autocomplete in Neovim"
date: 2022-01-23T15:30:39Z
draft: false
---

The most basic get up and running guide for some autocomplete goodness in neovim.

Alternatively this can be looked at as a guide to getting a similar vim experience to vs-code without the overhead of an entire chromium instance.

# Setup

First you want to make sure the below prereq's are installed:

1. neovim >= 0.6 - [Install Guide](https://github.com/neovim/neovim/wiki/Installing-Neovim)
    * **NOTE** on ubuntu I simply went for the solution of building from source

2. vimplug - [Install Guide](https://github.com/junegunn/vim-plug#installation)

3. nodejs - Install using either [nvm](https://github.com/nvm-sh/nvm#installing-and-updating) or directly from [nodejs](https://nodejs.org/en/download/)

4. yarn - run the following after installing node `npm i -g yarn`

# Config

Once above tools are installed we're good to go.

Now we simply run the below command:

```shell
$ mkdir -p $HOME/.config/nvim
$ nvim $HOME/.config/nvim/init.vim
```

Paste the following config in the above file:


```vim
call plug#begin('~/.vim/plugged')
Plug 'neoclide/coc.nvim', {'branch': 'release'}
Plug 'neoclide/coc.nvim', {'do': 'yarn install --frozen-lockfile'}
call plug#end()

nmap <silent> gd <Plug>(coc-definition)
```

After dropping that in the `init.vim` file, either close and reopen neovim, or run `:source %` and then do `:PlugInstall`

# Servers

You are now ready to install an extension to get a language server running.

Have a browse of the available [extensions](https://github.com/neoclide/coc.nvim/wiki/Using-coc-extensions#implemented-coc-extensions)

Let's setup a javascript/typescript server as an example.

Open neovim and run the following `:CocInstall coc-tsserver`

Go to your home/project dir and run below commands:

```shell
$ mkdir js-test
$ touch main.js
```

Then we can write out a file like below

```javascript
const obj = { foo: 'bar' };

console.log(obj.foo);
```

Which should give you a nice popup with autocomplete when writing out above code, see screenshot:

![auto-complete](/neovim-cmp.png)

# 🎉

You have now (hopefully) successfully managed to setup neovim with LSP and autocomplete. If you happened to run into any issues, please reach out to me on twitter [@theis_nielsen](https://twitter.com/theis_nielsen)


