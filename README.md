# terminal-viewport

Keeps a reply within one screen of the terminal.

## Install

Claude Code:

```
/plugin marketplace add HotariTobu/terminal-viewport
/plugin install terminal-viewport@terminal-viewport-marketplace
```

Codex:

```
codex plugin marketplace add HotariTobu/terminal-viewport
codex plugin add terminal-viewport@terminal-viewport-marketplace
```

## Usage

```
/terminal-viewport:fit What breaks if the token expires mid-upload?
/terminal-viewport:fit
```

With a message, it is answered as if typed on its own. Only the length changes. With nothing after it, the previous reply is cut to fit.
