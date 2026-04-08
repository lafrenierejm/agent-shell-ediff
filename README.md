# agent-shell-ediff

Replace `agent-shell-diff` with an ediff-based interface. File changes
proposed by agent-shell are displayed in a side-by-side ediff session
with full syntax highlighting. On quit you are prompted to accept or
reject the change.

## Requirements

- Emacs 24.3+
- [agent-shell](https://github.com/anthropics/claude-code/tree/main/packages/agent-shell)

## Installation

### use-package + straight.el

```elisp
(use-package agent-shell-ediff
  :straight (:host github :repo "cassandracomar/agent-shell-ediff")
  :after agent-shell
  :custom
  (agent-shell-ediff-quick-quit t)
  :config
  (agent-shell-ediff-mode 1))
```

### use-package (manual load path)

```elisp
(use-package agent-shell-ediff
  :load-path "~/.emacs.d/site-lisp/agent-shell-ediff"
  :after agent-shell
  :custom
  (agent-shell-ediff-quick-quit t)
  :config
  (agent-shell-ediff-mode 1))
```

### Manual

Clone the repository and add it to your load path:

```sh
git clone https://github.com/cassandracomar/agent-shell-ediff ~/.emacs.d/site-lisp/agent-shell-ediff
```

```elisp
(add-to-list 'load-path "~/.emacs.d/site-lisp/agent-shell-ediff")
(require 'agent-shell-ediff)
(setq agent-shell-ediff-quick-quit t)
(agent-shell-ediff-mode 1)
```

## Usage

Enable the mode globally:

```elisp
(agent-shell-ediff-mode 1)
```

Disable it to restore the default `agent-shell-diff` behavior:

```elisp
(agent-shell-ediff-mode -1)
```

Or toggle interactively with `M-x agent-shell-ediff-mode`.

## Configuration

- `agent-shell-ediff-quick-quit` -- when non-nil, `q` in the ediff
  control buffer calls `agent-shell-ediff-quit` (skips the extra ediff
  quit confirmation). Works with evil-mode. Default: `nil`.

## Key bindings

Inside an ediff session the standard ediff bindings apply. With
`agent-shell-ediff-quick-quit` enabled, `q` skips the ediff quit
confirmation and goes straight to the accept/reject prompt.

## License

Copyright (C) 2026 Cassandra Comar. See source for details.
