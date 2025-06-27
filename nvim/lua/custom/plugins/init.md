
-- You can add your own plugins here or in other files in this directory!
--  I promise not to create any merge conflicts in this directory :)
--
-- See the kickstart.nvim README for more information

return {
  require 'custom.plugins.auto-session',
  require 'custom.plugins.autopairs-ts',
  require 'custom.plugins.code-companion',
  require 'custom.plugins.codeium',
  require 'custom.plugins.color-scheme',
  require 'custom.plugins.lazygit',
  require 'custom.plugins.lualine',
  require 'custom.plugins.mini',
  require 'custom.plugins.neoscroll',
  require 'custom.plugins.neotest',
  require 'custom.plugins.smear-cursor',
  require 'custom.plugins.tabs',
  require 'custom.plugins.tpipeline',
  require 'custom.plugins.trouble-logs',
  require 'custom.plugins.ufo',

  {
    'folke/noice.nvim',
    event = 'VeryLazy',
    opts = {},
    dependencies = {
      'MunifTanjim/nui.nvim',
      'rcarriga/nvim-notify',
    },
  },

  -- Add indentation guides even on blank lines
  {
    'lukas-reineke/indent-blankline.nvim',
    main = 'ibl',
    opts = {
      indent = { char = '┊' },
      scope = { enabled = false },
    },
    -- cond = false,
  },

  -- highlight css colors
  {
    'brenoprata10/nvim-highlight-colors',
    ft = { 'css' },
    config = true,
    lazy = true,
  },

  {
    'max397574/better-escape.nvim',
    config = function()
      require('better_escape').setup()
    end,
  },
}
