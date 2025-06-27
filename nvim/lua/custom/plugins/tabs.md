
return {
  {
    'akinsho/bufferline.nvim',
    version = '*',
    dependencies = 'nvim-tree/nvim-web-devicons',
    config = function()
      require('bufferline').setup {
        options = {
          offsets = {
            {
              filetype = 'neo-tree',
              text = 'File Explorer',
              text_align = 'center',
              separator = true,
            },
          },
          mode = 'buffers', -- Mostra buffers como abas
          diagnostics = 'nvim_lsp', -- Mostra erros/avisos
          show_buffer_close_icons = true,
          show_close_icon = true,
          separator_style = 'slant',
        },
      }

      -- Atalhos para navegar entre abas (como no VSCode)
      vim.keymap.set('n', '<Tab>', ':BufferLineCycleNext<CR>', { desc = 'Next buffer' })
      vim.keymap.set('n', '<S-Tab>', ':BufferLineCyclePrev<CR>', { desc = 'Previous buffer' })
      vim.keymap.set('n', '<leader>o', '<Cmd>BufferLineCloseRight<CR>', { desc = 'Close all buffers to the right' })
      vim.keymap.set('n', '<leader>O', '<Cmd>BufferLineCloseLeft<CR>', { desc = 'Close all buffers to the left' })
    end,
  },
}
