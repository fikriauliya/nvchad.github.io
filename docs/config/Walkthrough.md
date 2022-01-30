- (NOTE : Make sure you know basic lua , if not then [check](https://nvchad.github.io/getting-started/learn-lua) ).
- Make sure that you read sections in config (in the sidebar of this site) orderwise.

## Structure

NvChad comes with the following file / folder structure. [An up-to-date & full tree can be viewed in the repo](https://github.com/NvChad/NvChad/)

```tree

├── init.lua
│
├── lua
│   ├── colors
│   │   ├── highlights.lua
│   │   └── init.lua (i)
│   │
│   ├── core
│   │   ├── autocmds.lua
│   │   ├── default_config.lua
│   │   ├── mappings.lua
│   │   ├── options.lua
│   │   └── utils.lua (i)
|   |
│   ├── custom
│   │   ├── chadrc.lua
│   │   ├── init.lua
│   │   ├── more files, dirs
│   │
│   ├── plugins
│   │    ├── init.lua
│   │    ├── packerInit.lua
│   │    └── configs
│   │        ├── bufferline.lua
│   │        ├── others.lua
│   │        └── <many more plugin configs>

```

- The file names in the tree with (i) are meant to be ignored , i.e the user doesnt need to look at them. I assume you have basic lua knowledge The lua code in those files might fret you or look very complex / scare you from NvChad xD.

## Walkthrough

- Letss goooo!

![chad](https://media.discordapp.net/attachments/610012463907209227/891016498733256774/869951078962196571.png)
![lessgooo](https://cdn.discordapp.com/attachments/610012463907209227/891011437810577480/863483056531046450.png)

## Init.lua

- NvChads's config has a lua dir and init.lua.
- The init.lua basically loads the core config and custom config.
- pcall is usually used for error handling. check [https://www.lua.org/pil/8.4.html](lua docs) for more info.

## Themes

- First copy example chadrc in lua/custom/, make sure it has the theme table
- leader + th (leader is space in our config)

## Mappings

- leader + ch 

## Default general options

- This file is core/default_config.lua
- The table below contain all the default options for various stuffs in NvChad.

For example :

```lua
M.options = {}
M.ui = {}
M.plugins = {}
M.mappings = {} has general mappings
M.mappings.plugins = {} has plugin related mappings
```
# Plugins

- The lua/plugins dir contains three files , init.lua , packerInit.lua and the configs dir.
- packerInit: this file is used for defining packer's init stuff , so things like clone_timeout , compile_on_sync , etc and other packer related options are mentioned here.
- init.lua : is basically the packer config , it calls packerInit first and then following with definitions of other plugins + their configs'
- For example to add a plugin , packer uses this format :

```lua
use {
  "org or username/reponame",
  config = function()
    path to config ( require it)
  end
}

-- example
 use {
   "max397574/better-escape.nvim",
    config = function()
       require("plugins.configs.better_escape")
    end
}
```
- configs dir : most default plugins's configs are stored here!!