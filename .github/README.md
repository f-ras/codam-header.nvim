<h1 align="center">Codam Header for Neovim</h1>

This extension provides the Codam header integration in Neovim. The original 42 re-write is found at [42-header.nvim](https://github.com/Diogo-ss/42-header.nvim).

```bash
# ************************************************************************** #
#                                                                            #
#                                                        ::::::::            #
#   neovim-codam-header                                :+:    :+:            #
#                                                     +:+                    #
#   By: fras <fras@student.codam.nl>                 +#+                     #
#                                                    +#+                     #
#   Created: 2024/05/20 16:33:33 by fras          #+#    #+#                 #
#   Updated: 2024/05/26 00:33:49 by fras          ########   odam.nl         #
#                                                                            #
# ************************************************************************** #
```

## ✨ Features

- Command: `Stdheader`
- Auto update on save (optional)
- Supports `commentstring`
- Supports Git

## 🎈 Setup

<details>
  <summary>📦 Packer.nvim</summary>

```lua
use {
  "f-ras/codam-header.nvim",
  cmd = { "Stdheader" },
  config = function()
    require "codamheader"setup {
      default_map = true, -- Default mapping <F1> in normal mode.
      auto_update = true, -- Update header when saving.
      user = "username", -- Your user.
      mail = "your@email.com", -- Your mail.
    -- add other options.
    }
  end,
}
```

</details>

<details>
  <summary>💤 Lazy.nvim</summary>

Create a file 'codam-header.lua' in ~/.config/nvim/plugins/ with the following content:

```lua
return
{
  "f-ras/codam-header.nvim",
  cmd = { "Stdheader" },
  keys = { "<F1>" },
  opts = {
    default_map = true, -- Default mapping <F1> in normal mode.
    auto_update = true, -- Update header when saving.
    user = "username", -- Your user.
    mail = "your@email.com", -- Your mail.
    -- add other options.
  },
  config = function(_, opts)
    require("codamheader").setup(opts)
  end,
}
```

</details>

## ⚙ Options

```lua
{
  ---Max header size (not recommended change).
  --length = 80,
  ---Header margin (not recommended change).
  --margin = 5,
  ---Activate default mapping (e.g. F1).
  default_map = true,
  ---Enable auto-update of headers.
  auto_update = true,
  ---Default user.name.
  user = "username",
  ---Default user.email.
  mail = "your@mail.com",
  ---ASCII art.
  --asciiart = { "---", "---", ... },
  ---Git config.
  git = {
    ---Enable Git support.
    enabled = false,
    ---PATH to the Git binary.
    bin = "git",
    ---Use global user.name, otherwise use local user.name.
    user_global = true,
    ---Use global user.email, otherwise use local user.email.
    email_global = true,
  },
}
```

## 🌐 User and Mail

`user` and `mail` can be defined using global variables.

```lua
vim.g.user = "username"
vim.g.mail = "your@mail.com"
```

> **_NOTE:_** The order of priority: `global variables` > `git config (if support enabled)` > `user config`.
