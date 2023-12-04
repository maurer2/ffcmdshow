# ffcmdshow

Add some feline flair to the [Powerlevel10k](https://github.com/romkatv/powerlevel10k) and [Spaceship Prompt](https://github.com/spaceship-prompt/spaceship-prompt) command line theme using emojis and [nerd-fonts](https://www.nerdfonts.com/cheat-sheet).

## Powerlevel10k

Changes need to be made in the `p10k.zsh` config file, which is automatically created in the user's home directory during the p10k installation, e.g. `/Users/$username/.p10k.zsh`.

### Positions

![All positions](./screenshot.png)

#### Before prompt

Add an emoji or unicode character to the left side of the prompt. Don't forget to add a space after the icon.

```javascript
typeset -g POWERLEVEL9K_LEFT_PROMPT_FIRST_SEGMENT_START_SYMBOL='🐈 '
```
```javascript
typeset -g POWERLEVEL9K_LEFT_PROMPT_FIRST_SEGMENT_START_SYMBOL=$'\uf61a '
```

#### os_icon replacement

Replace the default os-icon (apple) with an emoji or unicode character.

```javascript
typeset -g POWERLEVEL9K_OS_ICON_CONTENT_EXPANSION=$'🐈'
```
```javascript
typeset -g POWERLEVEL9K_OS_ICON_CONTENT_EXPANSION=$'\uf61a'
```

#### user defined prompt

Create an entire new custom section that contains the icon. In order to do that one needs to create a helper function. The helper function needs to start with `prompt_`. `b` and `i`-parameters are used for defining the colours. The `-i` parameter is necessary, so that the unicode variable is correctly parsed.

```javascript
function prompt_cat() {
  p10k segment -b 255 -f 0 -t '🐈'
}
```

```javascript
function prompt_cat() {
  p10k segment -b 255 -f 0 -i $'\uf61a'
}
```

In order to actually show the new custom section in the prompt it is necessary to add the function to the prompt list. The `prompt_`-part of the function name needs to be omitted.

```bash
typeset -g POWERLEVEL9K_LEFT_PROMPT_ELEMENTS=(
  os_icon                 # os identifier
  cat                     # cat section
  whoami                  # whoami
  dir                     # current directory
  vcs                     # git status
)
```

## Spaceship Prompt

Changes need to be made in the `.spaceshiprc.zsh` config file, which needs to be created in the user's home directory, e.g. `/Users/$username/.spaceshiprc.zsh`.

<img src="./screenshot-spaceship-prompt.webp" width=50% alt=" screenshot of spaceship prompt">

```bash
SPACESHIP_CHAR_SYMBOL="\uf61a"
SPACESHIP_CHAR_SUFFIX=" "
```
