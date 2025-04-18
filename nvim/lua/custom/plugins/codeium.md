
return {
  'Exafunction/codeium.nvim',
  dependencies = {
    'nvim-lua/plenary.nvim',
    'hrsh7th/nvim-cmp',
  },
  event = 'InsertEnter',
  config = function()
    require('codeium').setup {}

    -- Use autocmd para garantir que o plugin foi carregado antes de mapear
    vim.api.nvim_create_autocmd('User', {
      pattern = 'CodeiumLoaded',
      callback = function()
        vim.keymap.set('i', '<Tab>', function()
          return vim.fn['codeium#Accept']()
        end, { expr = true, silent = true, desc = 'Codeium Accept' })

        vim.keymap.set('i', '<C-[>', function()
          return vim.fn['codeium#CycleCompletions'](-1)
        end, { expr = true, silent = true, desc = 'Codeium Prev Suggestion' })

        vim.keymap.set('i', '<C-]>', function()
          return vim.fn
        end, { expr = true, silent = true, desc = 'Codeium Next Suggestion' })

        vim.keymap.set('i', '<C-x>', function()
          return vim.fn['codeium#Clear']()
        end, { expr = true, silent = true, desc = 'Codeium Clear' })
      end,
    })
  end,
}
