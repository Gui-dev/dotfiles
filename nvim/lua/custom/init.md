require 'custom.options.option'
require 'custom.keymaps.shortcuts'

require 'custom.options.markdown-disable'

vim.api.nvim_create_autocmd('VimLeavePre', {
  callback = function()
    -- Redefine o status original do tmux
    vim.fn.system 'tmux set-option status on'
    vim.fn.system 'tmux set-option -g status-left ""'
    vim.fn.system 'tmux set-option -g status-right ""'
    vim.fn.system 'tmux refresh-client -S'
  end,
})

