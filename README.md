# coc-hover-highlight-patch

For reasons that are not clear in one or two sentences,
the code blocks in the markdown document given in coc's floating window are
not highlighted correctly under Vim8.

This plugin allows it to be highlighted correctly.

This plugin was invented for the following reasons:

* Vim8's default markdown syntax file doesn't support code blocks highlighting,
  so I like to use https://github.com/plasticboy/vim-markdown to enhance it.
* Coc rejects `set filetype=markdown` and uses `runtime! syntax/markdown.vim`
  to render the contents of the floating window.
* But the `vim-markdown` logic for code blocks highlighting is in `ftplugin/markdown.vim`.
* Also, `vim-markdown` has [bug](plasticboy/vim-markdown#514) with popup-window.

The problem does involve a lot of parties,
such as coc, coc-rust-analyzer, vim-markdown, vim8, etc.
The reasons listed above may still be incomplete,
and I can't convince any party to solve the problem on their own,
so I wrote this dirty patch, I know it's ugly, but IT JUST WORKS!

Almost all the code for this plugin comes from `vim-markdown`.

If you encounter any problems while using it, please feel free to send me an issue.

## Usage:

Assuming you are using vim-plug, just put the following code in the appropriate place in vimrc(after `vim-markdown`):

```
Plug 'flw-cn/coc-hover-highlight-patch'
```

If you use another plugin manager, please check the documentation yourself.

## See also

* https://github.com/plasticboy/vim-markdown/issues/514
* https://github.com/fannheyward/coc-rust-analyzer/issues/374
* https://github.com/neoclide/coc.nvim/commit/0033e4e6249026191173024d52a6a135af578ebe?branch=0033e4e6249026191173024d52a6a135af578ebe&diff=unified#diff-7185cd5a5eaae4f5b948f5b1de6d9b95
