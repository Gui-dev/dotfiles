
return {
  {
    'catppuccin/nvim',
    name = 'catppuccin',
    priority = 1000,
    lazy = false,
    config = function()
      require('catppuccin').setup {
        flavour = 'mocha', -- ou 'latte', 'frappe', 'macchiato'
        integrations = {
          treesitter = true,
          cmp = true,
          gitsigns = true,
          telescope = true,
          which_key = true,
          indent_blankline = { enabled = true },
          native_lsp = {
            enabled = true,
            underlines = {
              errors = { 'undercurl' },
              hints = { 'undercurl' },
              warnings = { 'undercurl' },
              information = { 'undercurl' },
            },
          },
        },
      }
      vim.cmd.colorscheme 'catppuccin'
    end,
  },
}
