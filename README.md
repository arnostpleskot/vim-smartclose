vim-smartclose
============

Close Vim windows in a smart way!


Installation
------------

Place in *~/.vim/plugin/smartclose.vim* or in case of Pathogen:

    cd ~/.vim/bundle
    git clone https://github.com/szw/vim-smartclose.git

Please, don't forget to star the repository if you like (and use) the plugin. This will let me know
how many users it has and then how to proceed with further development :).


About
-----

SmartClose is a wise closing utility. What does it mean? SmartClose plugin distinguishes two kinds
of windows (the regular windows you use to work) and the auxiliary ones (a preview window,
a NERDTree panel, a quickfix window, etc). Basically, the plugin allows you to close a window
just with a single keystroke (`<F10>`). But if there are any auxiliary windows visible, it closes them
first (in the LIFO order). It means, you don't have to leave the current (regular) window to close
the auxiliary one. Just hit `<F10>` and you'll get it closed. If there are no auxiliary windows visible,
`<F10>` will close the current window (and a tab if it would be the last window in the tab, or the editor
itself, if it would be the last tab).

If you hit `<F10>` inside an auxiliary window, the window is closed immediately. And sometimes, the
same behavior could be desired inside regular windows too, right? Even, if there are visible
auxiliary ones, which will have the precedence, as said before. Therefore, the plugin provides you
a configurable delay time. By default, during the first second after entering a regular window,
hitting `<F10>` will close that window rather than any auxiliary ones.

In other words, the smart auxiliary windows closing feature is delayed about 1 sec. This way you
can move into a regular window you want to close, press `<F10>` immediately, and close it even if
there are open auxiliary windows on the screen. The delay can be adjusted or even disabled.

Usage
-----

SmartClose has only one command:

    :SmartClose

Also the plugin can define some default mappings if the user wants to. By default it maps to
`<F10>` in normal, insert, and visual modes. See [Configuration](#configuration) to get some
examples.

The banged version forces closing of the current window:

    :SmartClose!


<div id="configuration"></div>
Configuration
-------------

SmartClose is extremely handy with command mappings. By default it uses `<F10>` like here:

    nnoremap <silent><F10> :SmartClose<CR>
    vnoremap <silent><F10> :SmartClose<CR>
    inoremap <silent><F10> <C-[>:SmartClose<CR>

With these mappings you can hit `<F10>` any time, not only in normal mode.

Here are some plugin options:

* `smartclose_set_default_mapping`

    Whether SmartClose should set default mappings or not:

        let g:smartclose_set_default_mapping = 1


* `smartclose_set_mapping_with_bang`

    Whether SmartClose should set default mappings with banged version or not:

        let g:smartclose_set_mapping_with_bang = 0


* `smartclose_default_mapping_key`

    The default mappings key:

        let g:smartclose_default_mapping_key = '<F10>'


* `smartclose_delay`

    Sets the delay of smart closing auxiliary windows (in miliseconds). After entering a new window 
    `<F10>` will start closing auxiliary windows rather than that window only after this period. 
    By default it's set to 0 (turned off).

        let g:smartclose_delay = 0


Author and License
------------------

SmartClose was written by Szymon Wrozynski and
[Contributors](https://github.com/szw/vim-smartclose/commits/master). It is licensed under the same
terms as Vim itself.

Copyright &copy; 2013-2014 Szymon Wrozynski and Contributors. See `:help license`
