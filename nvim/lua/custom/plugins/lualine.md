
return {
  'nvim-lualine/lualine.nvim',
  dependencies = { 'nvim-tree/nvim-web-devicons' },
  config = function()
    require('lualine').setup {
      options = {
        theme = 'catppuccin',
        section_separators = '',
        component_separators = '|',
        icons_enabled = true,
        globalstatus = false,
      },
      sections = {
        lualine_a = { 'mode' },
        lualine_b = {
          'branch', -- Nome do branch atual
          'diff', -- Mostra + - ~ do Git
        },
        lualine_c = {
          { 'filename', path = 1 },
        },
        lualine_x = {
          {
            'diagnostics', -- Mostra erros, warnings etc
            sources = { 'nvim_diagnostic' },
            sections = { 'error', 'warn', 'info', 'hint' },
            symbols = {
              error = ' ',
              warn = ' ',
              info = ' ',
              hint = ' ',
            },
            colored = true,
            update_in_insert = false,
            always_visible = false,
          },
        },
        lualine_y = { 'filetype' },
        lualine_z = { 'location' },
      },
    }
  end,
}
