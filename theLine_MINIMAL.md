# theLine_MINIMAL

### 🧩 Prerequisites
 *To replicate the terminal appearance as shown in the screenshots, please follow all the following steps. Otherwise, you may skip steps 1 and 2.*
1. **[Ubuntu Mono Nerd Font Regular ](https://github.com/ryanoasis/nerd-fonts/tree/master/patched-fonts/UbuntuMono/Regular)**
Or  **[Fira Code Nerd Font Regular](https://github.com/ryanoasis/nerd-fonts/tree/master/patched-fonts/FiraCode/Regular)** 

> [**Nerd Fonts**](https://github.com/ryanoasis/nerd-fonts/tree/master) is a project that patches developer targeted fonts with a high number of glyphs (icons), Specifically to add a high number of extra glyphs from popular 'iconic fonts' such as Font Awesome, Devicons, Octicons, and others.

2. **Black Box Terminal**: [[line/install Black Box|install and configure Black Box]]
3. **Z Shell (ZSH)** : [[line/install ZSH|install zsh]]
4. [Starship](https://starship.rs/) prompt
5. Configure starship_theLine_MINMAL theme
### ⚙️ Configure starship_theLine_MINIMAL theme
1. Open any text editor
2. Copy the next :
```toml
#--------[ LORENS OSMAN ]--------#


#--------[ starship_theLine_MINIMAL ]

format = """
${custom.directory}\
$git_branch\
$git_status\
[ |](fg:#ED333B bg:#2E2F38)\
[ ]()\

"""

#--------[COMMANDS]

[custom.directory]
description = "Replace the default directory command"
command = """echo "${PWD/$HOME/~}" """
style = "fg:#33dd2d bg:#2E2F38"
format = "[  󰉋 $output ]($style)"
when = "true"

#--------[GIT COMMANDS]

[git_branch]
symbol = " "
style = "fg:#e5e512 bg:#242424"
format = "[ $symbol$branch(:$remote_branch) ]($style)"

[git_status]
# disabled = true
style = "fg:#e5e512 bg:#242424"
staged = "STG:${count} " # nf-fa-check
modified = "MOD:${count} " # nf-fa-edit
# modified = "  ${count}" # nf-fa-pencil
renamed = "󰗧:${count} " # nf-md-cursor_text
untracked = "UN:${count} " # nf-fa-question
deleted = "DEL:${count} " # nf-fa-remove
conflicted = "✖:${count} " # nf-fa-flag
stashed = ":${count} " # nf-fa-bank
# stashed = "  ${count}" # nf-fa-inbox

ahead = "󰞙 ${count} " # nf-md-arrow_expand_up
behind = "󰞖 ${count} " # nf-md-arrow_expand_down
diverged = "󰡏 ${ahead_count} ${behind_count} " # nf-md-arrow_expand_vertical
# diverged = "󰯎 ${ahead_count} ${behind_count}" # nf-md-swap_vertical_bold
# ignore_submodules = true
format = "[ ([$staged](fg:47 bg:#242424)[$modified](fg:5 bg:#242424)$renamed[$untracked](blue bg:#242424)[$deleted](fg:9 bg:#242424)$conflicted$stashed$ahead_behind )]($style)"

[git_state]
# disabled = true
style = "bg:color_git_state fg:color_foreground_dark"
rebase = "rebasing"
merge = "merging"
revert = "reverting"
cherry_pick = " picking" # nf-fae-cherry
bisect = "bisecting"
am = "am'ing"
am_or_rebase = "am/rebase"
format = '[ $state($progress_current/$progress_total) ]($style)'
```
3. Save the file in `toml` format, with the name `starship_theLine_MINIMAL.toml`
4. Open the `.zshrc` file using any text editor
5. Before the line `eval "$(starship init zsh)"` add the line `export STARSHIP_CONFIG=~/path/starship_theLine_MINIMAL.toml`Be sure to replace `path` with the actual location where you saved the `starship_theLine_MINIMAL.toml` file
6. Reload your terminal
7. Enjoy!
### 🖼️ Screenshots


![[line/assets/minimal/Screenshot from 2024-01-09 15-52-26.png]]

![[line/assets/minimal/Screenshot from 2024-01-09 15-53-37.png]]

![[line/assets/minimal/Screenshot from 2024-01-09 15-50-27.png]]