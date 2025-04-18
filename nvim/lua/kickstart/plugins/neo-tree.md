
-- Neo-tree is a Neovim plugin to browse the file system
-- https://github.com/nvim-neo-tree/neo-tree.nvim

return {
  'nvim-neo-tree/neo-tree.nvim',
  version = '*',
  dependencies = {
    'nvim-lua/plenary.nvim',
    'nvim-tree/nvim-web-devicons', -- not strictly required, but recommended
    'MunifTanjim/nui.nvim',
  },

  config = function()
    require('nvim-web-devicons').setup { default = true }
    require('neo-tree').setup {
      close_if_last_window = true, -- Fecha se for o último buffer
      popup_border_style = 'rounded',
      enable_git_status = true,
      enable_diagnostics = true,

      default_component_configs = {
        icon = {
          folder_closed = '',
          folder_open = '',
          folder_empty = '',
          default = '',
          highlight = 'NeoTreeFileIcon',
        },
        name = {
          highlight = 'NeoTreeFileName',
        },
        modified = {
          symbol = '●',
          highlight = 'NeoTreeModified',
        },
        git_status = {
          symbols = {
            added = '',
            modified = '',
            deleted = '',
            renamed = '󰁕',
            untracked = '',
            ignored = '',
            unstaged = '',
            staged = '',
            conflict = '',
          },
        },
      },

      filesystem = {
        window = {
          mappings = {
            ['\\'] = 'close_window',
          },
        },
        filtered_items = {
          visible = true,
          hide_dotfiles = false,
          hide_gitignored = false,
        },
        follow_current_file = {
          enabled = true,
        },
        group_empty_dirs = true,
        hijack_netrw_behavior = 'open_default',
      },

      buffers = {
        follow_current_file = {
          enabled = true,
        },
      },

      event_handlers = {
        {
          event = 'neo_tree_buffer_enter',
          handler = function()
            vim.opt_local.signcolumn = 'auto'
          end,
        },
      },
    }

    -- Atalho para abrir facilmente
    vim.keymap.set('n', '<leader>e', ':Neotree toggle<CR>', { desc = 'Toggle Neo-tree' })
  end,

  cmd = 'Neotree',
  keys = {
    { '\\', ':Neotree reveal<CR>', desc = 'NeoTree reveal', silent = true },
  },
}
