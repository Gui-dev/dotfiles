
-- Desativa diagnostics em arquivos Markdown usando o método recomendado
vim.api.nvim_create_autocmd('FileType', {
  pattern = 'markdown',
  callback = function()
    local bufnr = vim.api.nvim_get_current_buf()
    vim.diagnostic.disable(bufnr)
  end,
})
