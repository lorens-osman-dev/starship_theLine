# theLine_CHAIN

### 🧩 Prerequisites
 *To replicate the terminal appearance as shown in the screenshots, please follow all the following steps. Otherwise, you may skip steps 1 and 2.*
1. **[Ubuntu Mono Nerd Font Regular ](https://github.com/ryanoasis/nerd-fonts/tree/master/patched-fonts/UbuntuMono/Regular)**
Or  **[Fira Code Nerd Font Regular](https://github.com/ryanoasis/nerd-fonts/tree/master/patched-fonts/FiraCode/Regular)** 

> [**Nerd Fonts**](https://github.com/ryanoasis/nerd-fonts/tree/master) is a project that patches developer targeted fonts with a high number of glyphs (icons), Specifically to add a high number of extra glyphs from popular 'iconic fonts' such as Font Awesome, Devicons, Octicons, and others.

2. **Black Box Terminal**: [[line/install Black Box|install and configure Black Box]]
3. **Z Shell (ZSH)** : [[line/install ZSH|install zsh]]
4. [Starship](https://starship.rs/) prompt
5. Configure starship_theLine_CHIN theme
### ⚙️ Configure starship_theLine_CHAIN theme
1. Open any text editor
2. Copy the next :
```toml
#--------[ LORENS OSMAN ]--------#


#--------[ starship_theLine_CHAIN ]

format = """
$username\
[━━━](fg:#4b494f)\
$hostname\
[━━━](fg:#4b494f )\
${custom.directory}\
[━━━](fg:#4b494f)\
$fill\
$git_branch\
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
symbol="━"
style = "fg:#4b494f   "

[line_break]
disabled = false

[character]
success_symbol ='[━━](bold fg:#474a85)'
error_symbol ='[✖ ](bold red)'

#--------[GIT COMMANDS]

[git_branch]
symbol = "  "
style = "white bold bg:#857847 "
format = "[$symbol$branch(:$remote_branch) ]($style)"

```
3. Save the file in `toml` format, with the name `starship_theLine_CHAIN.toml`
4. Open the `.zshrc` file using any text editor
5. Before the line `eval "$(starship init zsh)"` add the line `export STARSHIP_CONFIG=~/path/starship_theLine_CHAIN.toml`Be sure to replace `path` with the actual location where you saved the `starship_theLine_CHAIN.toml` file
6. Reload your terminal
7. Enjoy!
### 🖼️ Screenshots

![[line/assets/chian/Screenshot from 2024-01-09 16-00-15.png]]

![[line/assets/chian/Screenshot from 2024-01-09 16-00-30.png]]

![[line/assets/chian/Screenshot from 2024-01-09 15-59-28.png]]

![[line/assets/chian/Screenshot from 2024-01-09 16-00-56.png]]

![[line/assets/chian/Screenshot from 2024-01-09 16-01-11.png]]
