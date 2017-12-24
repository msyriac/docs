# Emacs



## Visit git revisions


Open a buffer with a specific git revision by entering `C-x v ~`
and typing the mae of the branch (e.g. `upstream/master`).

[More here](https://stackoverflow.com/questions/25420282/using-emacs-and-magit-to-visit-a-file-in-given-commit-branch-etc)

## Defining keyboard macros

If you do a task in emacs repeatedly, e.g. type the same set of module
imports in python scripts, you can compress that task into a keyboard macro.

- `M-x start-kbd-macro` to start macro recording
- do your stuff
- `M-x kmacro-end-or-call-macro` to end macro
- `M-x kmacro-name-last-macro` to name macro
- `M-x insert-kbd-macro` to save macro

[More here](https://emacs.stackexchange.com/questions/70/how-to-save-a-keyboard-macro-as-a-lisp-function)