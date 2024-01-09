# theLine_DASHED

### 🧩 Prerequisites
 *To replicate the terminal appearance as shown in the screenshots, please follow all the following steps. Otherwise, you may skip steps 1 and 2.*
1. **[Ubuntu Mono Nerd Font Regular ](https://github.com/ryanoasis/nerd-fonts/tree/master/patched-fonts/UbuntuMono/Regular)**
Or  **[Fira Code Nerd Font Regular](https://github.com/ryanoasis/nerd-fonts/tree/master/patched-fonts/FiraCode/Regular)** 

> [**Nerd Fonts**](https://github.com/ryanoasis/nerd-fonts/tree/master) is a project that patches developer targeted fonts with a high number of glyphs (icons), Specifically to add a high number of extra glyphs from popular 'iconic fonts' such as Font Awesome, Devicons, Octicons, and others.

2. **Black Box Terminal**: [[line/install Black Box|install and configure Black Box]]
3. **Z Shell (ZSH)** : [[line/install ZSH|install zsh]]
4. [Starship](https://starship.rs/) prompt
5. Configure starship_theLine_DASHED theme
### ⚙️ Configure starship_theLine_DASHED theme
1. Open any text editor
2. Copy the next :
```toml
#--------[ LORENS OSMAN ]--------#


#--------[ starship_theLine_DASHED]

format = """${custom.user}\
[---](#eddf31 bold)\
${custom.host}\
[--](fg:#4b494f bold)\
${custom.dir}\
$fill\
$git_branch\
$git_status\
$git_state\
$line_break\
$username\
$hostname\
${custom.directory}\
$line_break\
$character
"""


#--------[CUSTOM COMMANDS]

[custom.directory]
description = "Replace the default directory command"
command = """echo "${PWD/$HOME/~}" """
style = "fg:#33dd2d "
format = "[  󰉋 $output]($style)"
when = "true"

[custom.dir]
description = "Dashes above directory "
command = """printf '%*s' "$(echo $(( $(pwd | sed "s|$HOME|~|" | wc -c) + 1 )))" '' | tr ' ' '-'"""
style = "fg:#33dd2d"
format = "[$output]($style)"
when = "true"

[custom.user]
description = "Dashes above username"
command = """printf '%*s' "$(echo $(echo $USER | tr -d '\n' | wc -c)+ 2)" '' | tr ' ' '-'"""
style = "#313fed bold"
format = "[$output]($style)"
when = "true"

[custom.host]
description = "Dashes above hostname"
command = """printf '%*s' "$(echo $(echo $HOST | tr -d '\n' | wc -c))" '' | tr ' ' '-'"""
style = "red bold"
format = "[$output]($style)"
when = "true"


#--------[COMMANDS]

[hostname]
ssh_only = false
format = '[$ssh_symbol](bold blue)[$hostname](bold red)'
trim_at = '.companyname.com'
disabled = false

[username]
style_user = '#313fed bold'
style_root = 'black bold'
format = '[ $user]($style)[ @ ](#eddf31 bold)'
disabled = false
show_always = true

[fill]
symbol="-"
style = "fg:#4b494f bold"

[line_break]
disabled = false

[character]
success_symbol ='[➜ ](bold green)'
error_symbol ='[✖ ](bold red)'

#--------[GIT COMMANDS]

[git_branch]
symbol = " "
style = "fg:#e5e512 bg:#4b494f"
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
3. Save the file in `toml` format, with the name `starship_theLine_DASHED.toml`
4. Open the `.zshrc` file using any text editor
5. Before the line `eval "$(starship init zsh)"` add the line `export STARSHIP_CONFIG=~/path/starship_theLine_DASHED.toml`Be sure to replace `path` with the actual location where you saved the `starship_theLine_DASHED.toml` file
6. Reload your terminal
7. Enjoy!
### 🖼️ Screenshots

![Screenshot from 2024-01-09 16-04-38.png](assets/dashed/Screenshot%20from%202024-01-09%2016-04-38.png)

![Screenshot from 2024-01-09 16-04-38.png](assets/dashed/Screenshot%20from%202024-01-09%2016-04-48.png)

![Screenshot from 2024-01-09 16-04-38.png](assets/dashed/Screenshot%20from%202024-01-09%2016-05-07.png)

![Screenshot from 2024-01-09 16-04-38.png](assets/dashed/Screenshot%20from%202024-01-09%2016-04-16.png)

![Screenshot from 2024-01-09 16-04-38.png](assets/dashed/Screenshot%20from%202024-01-09%2016-03-45.png)
