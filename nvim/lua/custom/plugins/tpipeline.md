
return {
  {
    'vimpostor/vim-tpipeline',
    lazy = false,
    init = function()
      vim.g['tpipeline_autoembed'] = 1
      vim.g['tpipeline_autoembed_term'] = 1
      vim.g['tpipeline_clearstl'] = 1
    end,
  },
}
