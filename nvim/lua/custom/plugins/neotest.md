
return {
  {
    'nvim-neotest/neotest',
    dependencies = {
      'nvim-neotest/nvim-nio',
      'nvim-lua/plenary.nvim',
      'antoinemadec/FixCursorHold.nvim',
      'nvim-treesitter/nvim-treesitter',
      'marilari88/neotest-vitest',
      'nvim-neotest/neotest-jest',
      'thenbe/neotest-playwright',
    },

    keys = {
      { '<leader>tr', '<cmd>Neotest run<cr>', desc = 'Run neotest test' },
      { '<leader>ti', '<cmd>Neotest output<cr>', desc = 'Run neotest output' },
      { '<leader>ts', '<cmd>Neotest summary<cr>', desc = 'Run neotest summary' },
      { '<leader>ta', '<cmd>lua require("neotest").run.run({ suite = true })<cr>', desc = 'Run all tests' },
    },

    config = function()
      require('neotest').setup {
        adapters = {
          require 'neotest-vitest' {
            env = { NODE_ENV = 'test' },
          },
          require 'neotest-jest' {
            jestCommand = 'npm test --',
            jestConfigFile = 'custom.jest.config.ts',
            env = { CI = true },
            cwd = function(path)
              return vim.fn.getcwd()
            end,
          },
          require('neotest-playwright').adapter {
            options = {
              persist_project_selection = true,
              enable_dynamic_test_discovery = true,
            },
          },
        },
      }
    end,
  },
}
