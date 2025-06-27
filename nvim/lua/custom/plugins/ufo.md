
return {
  {
    'kevinhwang91/nvim-ufo',
    event = 'BufReadPost',
    dependencies = {
      'kevinhwang91/promise-async',
      'nvim-treesitter/nvim-treesitter',
    },
    config = function()
      vim.o.foldcolumn = '1' -- Mostra coluna lateral com setas
      vim.o.foldlevel = 99 -- Expande tudo por padrão
      vim.o.foldlevelstart = 99
      vim.o.foldenable = true -- Ativa fold ao abrir arquivos

      require('ufo').setup {
        provider_selector = function(_, _, _)
          return { 'treesitter', 'indent' }
        end,
      }
    end,
  },
}
