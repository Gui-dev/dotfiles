set -g default-terminal "screen-256color"
set -ga terminal-overrides ',*:Tc' # this is for 256 color
set -ga terminal-overrides '*:Ss=\E[%p1%d q:Se=\E[ q' # this is for the cursor shape

set-option -sa terminal-features ',xterm-256color:RGB'

set -g status on
set -g status-interval 1
set -g status-justify centre
set -g status-left-length 60
set -g status-right-length 120
set -g status-left ''
set -g status-right '#[fg=yellow]#H #[fg=cyan]%Y-%m-%d %H:%M'

set -g prefix C-a
unbind C-b
bind-key C-a send-prefix

unbind %
bind | split-window -h -c "#{pane_current_path}"

unbind '"'
bind - split-window -v -c "#{pane_current_path}"

unbind r
bind r source-file ~/.tmux.conf \; display "Reloaded!" 

bind -r j resize-pane -D 5
bind -r k resize-pane -U 5
bind -r l resize-pane -R 5
bind -r h resize-pane -L 5

bind -r m resize-pane -Z

set -g mouse on

set-window-option -g mode-keys vi

bind-key -T copy-mode-vi 'v' send -X begin-selection # start selecting text with "v"
bind-key -T copy-mode-vi 'y' send -X copy-selection # copy text with "y"

unbind -T copy-mode-vi MouseDragEnd1Pane # don't exit copy mode after dragging with mouse

# tpm plugin
set -g @plugin 'tmux-plugins/tpm'

# list of tmux plugins
set -g @plugin 'christoomey/vim-tmux-navigator' # for navigating panes and vim/nvim with Ctrl-hjkl
set -g @plugin 'jimeh/tmux-themepack' # to configure tmux theme
set -g @plugin 'tmux-plugins/tmux-resurrect' # persist tmux sessions after computer restart
set -g @plugin 'tmux-plugins/tmux-continuum' # automatically saves sessions for you every 15 minutes

set -g @themepack 'powerline/default/cyan' # use this theme for tmux

# set -g @plugin 'catppuccin/tmux#v2.1.3'
# set -g @catppuccin_flavor 'mocha' # latte, frappe, macchiato or mocha


set -g @resurrect-capture-pane-contents 'on' # allow tmux-ressurect to capture pane contents
set -g @continuum-restore 'on' # enable tmux-continuum functionality


# Initialize TMUX plugin manager (keep this line at the very bottom of tmux.conf)
run '~/.tmux/plugins/tpm/tpm'

bind-key -n C-l if-shell "$is_vim" "send-keys C-l"  "send-keys C-l"

