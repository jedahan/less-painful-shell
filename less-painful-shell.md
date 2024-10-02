---
paging: SLIDE=%d SLIDES=%d
author: USER=micro
---

# less painful shell

```zsh
echo $SHELL is pragmatic
```
---

# less painful shell

```zsh
echo $SHELL is pragmatic
echo $SHELL is arcane
```
---

# less painful shell

```zsh
echo $SHELL is pragmatic
echo $SHELL is arcane
echo $SHELL is fun
```

---

# less painful shell

```zsh
echo "$SHELL == $TERM?"
```
```zsh
[[ $SHELL = $TERM ]] && echo its the same || echo nope
```

---

# less painful shell

```zsh
echo "$SHELL != $TERM"
```

This is mostly about working with shell scripts.

Can do a followup about Terminals if folks are interested.

Do not feel bad if this distinction is unclear.

It is the nature of the beast.

---

# learning

> shell is like 7 languages, lets focus on 3

---

# learning

> shell is like 7 languages, lets focus on 3

1. commands 

```zsh
whence $SHELL
```

---

# learning

> shell is like 7 languages, lets focus on 3

1. commands `whence`
2. variables

```zsh
export WHENCE=$(whence $SHELL)
echo $WHENCE becomes ${WHENCE/bin/secret}
```

---

# learning

> shell is like 7 languages, focus on a few

1. commands `whence`
2. variables `echo ${WHENCE/bin/secret}`
3. control flow

```zsh
if [[ $SHELL == '/bin/zsh' ]]
then
  echo neat
fi
```

---

# learning

> shell is like 7 languages, focus on a few

1. commands `whence`
2. variables `echo ${WHENCE/bin/secret}`
3. control flow `if [[ $SHELL == '/bin/zsh' ]]; then echo neat; fi`

---

# learning part II

## For readers

* [jvns](https://jvns.ca)
* [dylanaraps](https://github.com/dylanaraps)
* beware dev.to/hackernoon
* [oils](https://www.oilshell.org/blog)

## For watchers

I dunno, your suggestions appreciated.  

---

# making

[tldr](https://tldr.sh)

```zsh
tldr --compact zsh | head --lines 15
```

---

# making

[tldr](https://tldr.sh) `tldr --compact zsh | head --lines 10`

read [Command Line Interface Guidelines](https://clig.dev) `open https://clig.dev`

```zsh
open https://clig.dev
```

---

# making

[tldr](https://tldr.sh) `tldr --compact zsh | head --lines 10`

read [Command Line Interface Guidelines](https://clig.dev) `open https://clig.dev`

lookup [explainshell](https://explainshell.com)

```zsh
command='file=$(echo `basename "$file"`)'
open "https://explainshell.com/explain?cmd=$command"
```
---

# making

[tldr](https://tldr.sh) `tldr --compact zsh | head --lines 10`

read [Command Line Interface Guidelines](https://clig.dev) `open https://clig.dev`

lookup [explainshell](https://explainshell.com) `open explainshell.com/explain?cmd=ls`

discuss `bash` vs `zsh` vs `dash` vs `oils` vs `nushell` vs `fish`

mention posix vs non-posix

---

# making - philosphy for avoiding pain

## run everything when unsure!

```zsh
podman run --rm --interactive ghcr.io/zsh-users/zsh:5.9 zsh -c \
'echo hello from $container $HOSTNAME'
```
---

# making - philosphy for avoiding pain

## run everything when unsure!

```zsh
podman run --rm --interactive ghcr.io/zsh-users/zsh:5.9 zsh -c \
'echo hello from $container $HOSTNAME'
```
yes, everything 😈

```zsh
podman run --rm --interactive ghcr.io/zsh-users/zsh:5.9 zsh -c \
'rm -rf --no-preserve-root / 2>/dev/null; whence -v ls || true'
```

---

# making - philosphy for avoiding pain

> An aside about frameworks and prompts (PSA to avoid OMZ)

## run everything when unsure!

`podman run --rm --interactive ghcr.io/zsh-users/zsh:5.9 zsh -c`

## restict feature use...

Not advocating for full posix sh, but shell has decades of cruft

## ...but avoid re-inventing features!

Features worth incorporating: `pipes`, `redirection`, `signals`, `long options`

## strict mode

```bash
set -euo pipefail
```

Its actually `set -e`, `set -u`, `set -o pipefail` 

Learn to set and unset options

---

# solidifying

philosophy
* long options
* good, bad and ugly of shellcheck 

materiality
* info() / trap()
* printf vs echo
* subshells and scope `$()` vs `()`, and why use `{}`
