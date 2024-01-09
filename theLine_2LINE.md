# theLine_2LINE

### 🧩 Prerequisites
 *To replicate the terminal appearance as shown in the screenshots, please follow all the following steps. Otherwise, you may skip steps 1 and 2.*
1. **[Ubuntu Mono Nerd Font Regular ](https://github.com/ryanoasis/nerd-fonts/tree/master/patched-fonts/UbuntuMono/Regular)**
Or  **[Fira Code Nerd Font Regular](https://github.com/ryanoasis/nerd-fonts/tree/master/patched-fonts/FiraCode/Regular)** 

> [**Nerd Fonts**](https://github.com/ryanoasis/nerd-fonts/tree/master) is a project that patches developer targeted fonts with a high number of glyphs (icons), Specifically to add a high number of extra glyphs from popular 'iconic fonts' such as Font Awesome, Devicons, Octicons, and others.

2. **Black Box Terminal**: [[line/install Black Box|install and configure Black Box]]
3. **Z Shell (ZSH)** : [[line/install ZSH|install zsh]]
4. [Starship](https://starship.rs/) prompt
5. Configure starship_theLine_2LINE theme
### ⚙️ Configure starship_theLine_2LINE theme
1. Open any text editor
2. Copy the next :
```toml
#--------[ LORENS OSMAN ]--------#

#--------[ theLine_2LINE ]
# use ubuntuMono Nerd Font Mono 9
format = """
${custom.user}\
[   ](fg:#4b494f underline )\
${custom.host}\
[   ](fg:#4b494f underline )\
${custom.dir}\
$fill\
${custom.git}\
[   ](fg:#4b494f underline )\
$line_break\
$username\
[   ](fg:#4b494f underline )\
$hostname\
[   ](fg:#4b494f underline )\
${custom.directory}\
$fill\
$git_branch\
[   ](fg:#4b494f underline )\
$line_break\
$character
"""


#--------[CUSTOM COMMANDS]--------#

[custom.directory]
description = "Replace the default directory command"
command = """echo "${PWD/$HOME/~}" """
style = "fg:#33dd2d underline"
format = "[󰉋 $output]($style)"
when = "true"

[custom.dir]
description = "Dashes of directory "
command = """printf '%*s' "$(echo $(( $(pwd | sed "s|$HOME|~|" | wc -c) + 1 )))" '' | tr ' ' '_'"""
style = "fg:#33dd2d underline"
format = "[$output]($style)"
when = "true"


[custom.git]
description = "Replace the branch name with dashes"
command = "git rev-parse --abbrev-ref HEAD 2>/dev/null | wc -m | tr -d '\\n' | xargs -I {} seq -s '_' {} | tr -d '[:digit:]'| awk '{print $0 \"___\"}'"
when = "git rev-parse --abbrev-ref HEAD 2>/dev/null"
shell = ["bash", "--noprofile", "--norc"]
style = "fg:#e5e513 underline"
format = "[$output]($style)"

[custom.user]
description = "Dashes of username"
command = """printf '%*s' "$(echo $(echo $USER | tr -d '\n' | wc -c))" '' | tr ' ' '_' """
style = "#313fed  underline"
format = "[$output]($style)"
when = "true"

[custom.host]
description = "Dashes of hostname"
command = 'printf "%*s" "$(echo $(echo $HOST | tr -d "\n" | wc -c))" "" | tr " " "_" '
style = "red underline"
format = "[$output]($style)"
when = "true"

#--------[COMMANDS]

[hostname]
ssh_only = false
format = '[$ssh_symbol](bold blue)[$hostname]( red underline)'
trim_at = '.companyname.com'
disabled = false

[username]
style_user = '#313fed underline'
style_root = 'black'
format = '[$user]($style)'
disabled = false
show_always = true

[fill]
symbol="⸏"
style = "fg:#4b494f underline"

[line_break]
disabled = false

[character]
success_symbol ='[](bold green)'
error_symbol ='[✖ ](bold red)'

#--------[GIT COMMANDS]

[git_branch]
symbol = "  "
style = "fg:#e5e513  underline"
format = "[$symbol$branch(:$remote_branch)]($style)"

```
3. Save the file in `toml` format, with the name `starship_theLine_2LINE.toml`
4. Open the `.zshrc` file using any text editor
5. Before the line `eval "$(starship init zsh)"` add the line `export STARSHIP_CONFIG=~/path/starship_theLine_2LINE.toml`Be sure to replace `path` with the actual location where you saved the `starship_theLine_2LINE.toml` file
6. Reload your terminal
7. Enjoy!
### 🖼️ Screenshots

![clusterSvg](assets/2line/Screenshot%20from%202024-01-09%2016-08-28.png)

![clusterSvg](assets/2line/Screenshot%20from%202024-01-09%2016-08-50.png)

![clusterSvg](assets/2line/Screenshot%20from%202024-01-09%2016-09-07.png)

![clusterSvg](assets/2line/Screenshot%20from%202024-01-09%2016-08-10.png)

![clusterSvg](assets/2line/Screenshot%20from%202024-01-09%2016-07-58.png)
