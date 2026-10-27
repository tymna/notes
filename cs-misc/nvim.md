Nvim - at first glance (for a young developer) not a very practical thing. So why bother? If vscode is simple and convenient. That was the first thought, but right after it I remembered that everything non-obvious is worth trying, especially if really experienced developers use it (although... there was way too much hype around nvim (on the other hand, lots of hype, but only a few actually use it)).

First I tried it for writing notes, then for coding. But I can say right away that tutorials are great. They speed up the process a lot, show the efficient features and so on (yes, documentation is cool, but... it's better not to start with it. Probably that's the philosophy to use AI with now, because everything is heading that way).
So `ff`, a color theme, basic shortcuts from GPT. And then I got to videos of how people use it, that you need to think through how you press keys, and that there are even games to learn it.

But that's the next story. First - what is it and why at all?
How I understand the philosophy:
- you speed up coding by using certain keys on the keyboard. Your hands are in a position where reaching all the combinations is as efficient as possible
- there are lots of combinations, they can be custom, but they're easy to remember because they're named directly ("c" - cut, "p" - paste)
- the goal - stop using the mouse
- there are several modes:
	- Normal Mode - controlling the editor itself
	- Insert Mode - writing text
	- Visual Mode - selecting text
	- Replace Mode - replacing text
	- Command Line Mode - running commands

Basic commands.
Normal Mode:
- h j k l - navigation
- gg - start, G - end
- 10gg - specific line
- dd, yy, p, u - delete, copy, paste, undo
- w ->, b <-, e - end of the word
- $ - end of the line
- f -> "()", t -> to, but not on
- , ;
Insert Mode:
- i - before the cursor
- a - after the cursor
- A - after, at the end of the line
- o - new line
- c - delete+insert
Visual Mode:
- v - enter mode
- V - all line
- ctrl+v - specific block
Replace Mode:
- r - one symbol
Command Line Mode:
- :w - save
- :q - quit
- :wq - save+quit
Search:
- / - front
- ? - back
- n / N - next / previous
- * / # - search under cursor
- :noh


Function navigation:
- ]] - next function
- [[ - previous function
LSP (via Mason/lspconfig):
- gd - go to definition
- gr - go to references
- K - docs for the function under the cursor
- :Telescope lsp_document_symbols - list of all functions in the file (needs Telescope)

Game to learn Vim:
https://vim-adventures.com/
https://www.vimgolf.com/
