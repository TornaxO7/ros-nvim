# ros-nvim

![Neovim](https://img.shields.io/badge/NeoVim-%2357A143.svg?&style=for-the-badge&logo=neovim&logoColor=white)
![ROS](https://img.shields.io/badge/ros-%230A0FF9.svg?style=for-the-badge&logo=ros&logoColor=white)

Ros plugin for neovim

## Installation

### lazy.nvim

```lua
require("lazy").setup({
...
    {
        'tadachs/ros-nvim',
        config = function() require("ros-nvim").setup({only_workspace = true}) end,
        dependencies = { "tadachs/mutils.nvim" },
    },
...
})
```

You have to install [treesitter](https://github.com/nvim-treesitter/nvim-treesitter) and
[telescope](https://github.com/nvim-telescope/telescope.nvim) separately. To install the
grammar for syntax highlighting run `TSInstall ros`.


## Features

- `Rosed` command with tab completion
- follow `$(find ...)` links in launch files
- show message and service definitions in floating windows
- (optional) telescope finder
- (optional) syntax highlighting for messages, services and actions using treesitter

## Example Setup

```lua
-- telescope finder
vim.keymap.set('n', '<leader>tr', '<cmd>Telescope ros ros<cr>', { noremap = true })

-- follow links in launch files
vim.keymap.set('n', '<leader>rol', function() require("ros-nvim.ros").open_launch_include() end, { silent = true, noremap = true })

-- show definition for messages/services in floating window
vim.keymap.set('n', '<leader>rdm', function() require("ros-nvim.ros").show_message_definition() end, { silent = true, noremap = true })
vim.keymap.set('n', '<leader>rds', function() require("ros-nvim.ros").show_service_definition() end, { silent = true, noremap = true })
```

## Contributors

- [darius1702](https://github.com/darius1702)
