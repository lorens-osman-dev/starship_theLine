# theLine_HEAVY

### 🧩 Prerequisites
 *To replicate the terminal appearance as shown in the screenshots, please follow all the following steps. Otherwise, you may skip steps 1 and 2.*
1. **[Ubuntu Mono Nerd Font Regular ](https://github.com/ryanoasis/nerd-fonts/tree/master/patched-fonts/UbuntuMono/Regular)**
Or  **[Fira Code Nerd Font Regular](https://github.com/ryanoasis/nerd-fonts/tree/master/patched-fonts/FiraCode/Regular)** 

> [**Nerd Fonts**](https://github.com/ryanoasis/nerd-fonts/tree/master) is a project that patches developer targeted fonts with a high number of glyphs (icons), Specifically to add a high number of extra glyphs from popular 'iconic fonts' such as Font Awesome, Devicons, Octicons, and others.

2. **Black Box Terminal**: [[line/install Black Box|install and configure Black Box]]
3. **Z Shell (ZSH)** : [[line/install ZSH|install zsh]]
4. [Starship](https://starship.rs/) prompt
5. Configure starship_theLine_HEAVY theme
### ⚙️ Configure starship_theLine_HEAVY theme
1. Open any text editor
2. Copy the next :
```toml
#--------[ LORENS OSMAN ]--------#


#--------[ starship_theLine_heavy ]

format = """
${custom.user}\
[___](fg:#4b494f underline )\
${custom.host}\
[___](fg:#4b494f underline)\
${custom.dir}\
[___](fg:#4b494f underline)\
${custom.git}\
$fill\
[___](fg:#4b494f underline)\
$line_break\
$username\
[   ](fg:#4b494f bg:#4b494f )\
$hostname\
[   ](fg:#4b494f bg:#4b494f)\
${custom.directory}\
[   ](fg:#4b494f bg:#4b494f)\
$git_branch\
${custom.bgfill}\
$line_break\
$character
"""

#--------[CUSTOM COMMANDS]

[custom.directory]
description = "Replace the default directory command"
command = """echo "${PWD/$HOME/~}" """
style = "white bold bg:#498547"
format = "[ 󰉋 $output ]($style)"
when = "true"

[custom.dir]
description = "Dashes above custom.directory "
command = """printf '%*s' "$(echo $(( $(pwd | sed "s|$HOME|~|" | wc -c) + 3 )))" '' | tr ' ' '_'"""
style = "fg:#33dd2d underline "
format = "[$output]($style)"
when = "true"

[custom.git]
description = "Dashes above branch name "
command = "git rev-parse --abbrev-ref HEAD 2>/dev/null | wc -m | tr -d '\\n' | xargs -I {} seq -s '_' {} | tr -d '[:digit:]'| awk '{print $0 \"____\"}'"
when = "git rev-parse --abbrev-ref HEAD 2>/dev/null"
shell = ["bash", "--noprofile", "--norc"]
style = "fg:#e5e513 underline"
format = "[$output]($style)"

[custom.user]
description = "Dashes above username"
command = """printf '%*s' "$(echo $(echo $USER | tr -d '\n' | wc -c))" '' | tr ' ' '_' """
style = "#313fed  underline"
format = "[$output]($style)"
when = "true"

[custom.host]
description = "Dashes above hostname"
command = 'printf "%*s" "$(echo $(echo $HOST | tr -d "\n" | wc -c))" "" | tr " " "_" '
style = "red underline"
format = "[$output]($style)"
when = "true"

[custom.bgfill]
command = 'echo '
style="fg:#4b494f bg:#4b494f"
when="true"
shell="sh"
format = "[$output\u001B\\[K]($style)"


#--------[COMMANDS]

[username]
style_user = 'white bold bg:#474a85'
style_root = 'black'
format = '[$user]($style)'
disabled = false
show_always = true

[hostname]
ssh_only = false
format = '[$ssh_symbol](bold blue)[$hostname]( white bold bg:#854747 )'
trim_at = '.companyname.com'
disabled = false

[fill]
symbol="_"
style = "fg:#4b494f underline  "

[line_break]
disabled = false

[character]
success_symbol ='[_](bold green)'
error_symbol ='[✖ ](bold red)'

#--------[GIT COMMANDS]

[git_branch]
symbol = "  "
style = "white bold bg:#857847 "
format = "[$symbol$branch(:$remote_branch) ]($style)"

```
3. Save the file in `toml` format, with the name `starship_theLine_HEAVY.toml`
4. Open the `.zshrc` file using any text editor
5. Before the line `eval "$(starship init zsh)"` add the line `export STARSHIP_CONFIG=~/path/starship_theLine_HEAVY.toml`Be sure to replace `path` with the actual location where you saved the `starship_theLine_HEAVY.toml` file
6. Reload your terminal
7. Enjoy!
### 🖼️ Screenshots


![[line/assets/heavy/Screenshot from 2024-01-09 16-06-14.png]]

![[line/assets/heavy/Screenshot from 2024-01-09 16-06-26.png]]

![[line/assets/heavy/Screenshot from 2024-01-09 16-05-54.png]]

![[line/assets/heavy/Screenshot from 2024-01-09 16-06-48.png]]

![[line/assets/heavy/Screenshot from 2024-01-09 16-07-01.png]]