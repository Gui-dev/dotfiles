
-- custom/keymaps/lsp.lua

local map = vim.keymap.set
local opts = { silent = true, noremap = true }

-- Go to definition
map('n', '<leader>gd', vim.lsp.buf.definition, { desc = 'Go to Definition' })

-- Go to declaration
map('n', '<leader>gD', vim.lsp.buf.declaration, { desc = 'Go to Declaration' })

-- Go to implementation
map('n', '<leader>gi', vim.lsp.buf.implementation, { desc = 'Go to Implementation' })

-- Go to type definition
map('n', '<leader>gt', vim.lsp.buf.type_definition, { desc = 'Go to Type Definition' })

-- Show references
map('n', '<leader>gr', require('telescope.builtin').lsp_references, { desc = 'Show References' })
