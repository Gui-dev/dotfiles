
return {
  {
    'neovim/nvim-lspconfig',
    opts = {
      servers = {
        biome = {
          settings = {
            biome = {
              -- Habilita a correção automática de erros
              -- (além de formatar)
              autoFix = true,
            },
          },
        },
      },
    },
  },
}
