# zsh-better-npm-completion

> Better completion for `npm`

<img src="demo.gif" width="690">

* Makes `npm install` recommendations from npm cache
* Makes `npm uninstall` recommendations from `dependencies`/`devDependencies`
* Shows detailed information on script contents for `npm run`
* Falls back to default npm completions if we don't have anything better

## Installation

### As an [Oh My ZSH!](https://github.com/robbyrussell/oh-my-zsh) custom plugin

Clone `zsh-better-npm-completion` into your custom plugins repo

```shell
git clone https://github.com/gentslava/zsh-better-npm-completion.git $ZSH_CUSTOM/plugins/zsh-better-npm-completion
```
Then load as a plugin in your `.zshrc`

```shell
plugins+=(zsh-better-npm-completion)
```

### Manually
Clone this repository somewhere (`~/.zsh-better-npm-completion` for example)

```shell
git clone https://github.com/gentslava/zsh-better-npm-completion.git ~/.zsh-better-npm-completion
```
Then source it in your `.zshrc`

```shell
source ~/.zsh-better-npm-completion/zsh-better-npm-completion.plugin.zsh
```

## Module Install Cache

When running `npm install rea<tab>`, it will perform an `npm search` for matching packages. In addition
it will look in your local npm cache directory for package suggestions. However building this list
can be pretty slow. This completion makes use of the zsh completion caching mechanism to cache the
module list if you have caching enabled.

We try to enable it by default, however if you have something
like below in your zshrc forces cache for all completions to be turned off.

```zsh
zstyle ':completion:*' use-cache off
```

To specifically turn npm cache back on, you may add the following:

```zsh
zstyle ':completion::complete:npm::' use-cache on
```

By default the cache will be valid for 1 hour. But can be modified by setting a cache policy like this:

```zsh
_npm_install_cache_policy() {
  # rebuild if cache is more than 24 hours old
  local -a oldp
  # See http://zsh.sourceforge.net/Doc/Release/Expansion.html#Glob-Qualifiers
  # Nmh+24 ... N == NULL_GLOB, m == modified time, h == hour, +24 == +24 units (i.e. [M]onth, [w]weeks, [h]ours, [m]inutes, [s]econds)
  oldp=( "$1"(Nmh+24) )
  (( $#oldp ))
}
zstyle ':completion::complete:npm::' cache-policy _npm_install_cache_policy
```

## Related

- [`zsh-nvm`](https://github.com/gentslava/zsh-nvm) - Zsh plugin for installing, updating and loading `nvm`
