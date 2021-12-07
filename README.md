# cmp-path

nvim-cmp source for filesystem paths.

# Setup

```lua
require'cmp'.setup {
  sources = {
    { name = 'path' }
  }
}
```

## Fork notes

Relative paths in code are tricky because sometimes the paths may be relative to the file referencing them, and other times they might be relative to the project root (e.g. `cwd`), depending on how they're being interpreted.

This fork modifies the behaviour in insert mode to use paths relative to `cwd` instead of the directory of the current buffer, unless the path is prefixed with `./`.

This makes things a little closer to how `<c-x><c-f>` and CoC work (with the exception of the `./` part) which suits my most common use case.

Ultimately I'd like to see what it's like if it could complete paths relative to the `cwd` and the current buffer. I.e. providing completions for both after the initial opening quotation and then narrowing down to paths that match either.
