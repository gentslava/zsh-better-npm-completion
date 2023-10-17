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

## Related

- [`zsh-nvm`](https://github.com/lukechilds/zsh-nvm) - Zsh plugin for installing, updating and loading `nvm`
- [`gifgen`](https://github.com/lukechilds/gifgen) - Simple high quality GIF encoding
