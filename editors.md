### Editor

* Trailing whitespace makes no sense and make noises in git commits. It's very often annoyed when reviewing code. It's the best practice to trim it before saving file.

  ![](http://lh5.ggpht.com/_qSmJ0dW70FE/TPfBQjvbHQI/AAAAAAAAAWA/U7BUO-LzHwU/git%20diff.png)

  * For sublime users, go to Preferences -> Settings - User

        ```
        "tab_size": 2,
        "detect_indentation": false,
        "translate_tabs_to_spaces": true,
        "trim_trailing_white_space_on_save": true
        ```
  * For vim users, add this inside your .vimrc

        ```
        " Strip trailing whitespace
        function! <SID>StripTrailingWhitespaces()
            " Preparation: save last search, and cursor position.
            let _s=@/
            let l = line(".")
            let c = col(".")
            " Do the business:
            %s/\s\+$//e
            " Clean up: restore previous search history, and cursor position
            let @/=_s
            call cursor(l, c)
        endfunction
        autocmd BufWritePre * :call <SID>StripTrailingWhitespaces()
        ```