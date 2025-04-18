
return {
  'echasnovski/mini.move',
  version = '*',
  config = function()
    require('mini.move').setup {
      mappings = {
        -- Modo visual: mover seleção
        left = '<M-h>',
        right = '<M-l>',
        down = '<M-j>',
        up = '<M-k>',

        -- Modo normal: mover linha atual
        line_left = '<M-h>',
        line_right = '<M-l>',
        line_down = '<M-j>',
        line_up = '<M-k>',
      },
    }
  end,
}
