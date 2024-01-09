## Introduction

The Z Shell (Zsh) is an interactive Unix  shell that can be used as a command interpreter for shell scripting. It is an extended Bourne shell with numerous improvements, including some Bash, ksh, and tcsh features.

Some of the benefits Zsh offers are command-line completion, shared history, improved globbing, intelligent tab completion, spelling correction, and a rich set of plugins and themes.

**In this tutorial, you will learn to install and configure the Z Shell on Ubuntu.**
## install Zsh on Ubuntu
### Step 1: Update the System Repository

Update the system package repository to get the latest program version available. Open the terminal and run the following command:

```sh
sudo apt update
```

Enter the administrator password when prompted and press **Enter**. Wait for the process to complete.

Updating the package repository ensures that your system has the most up-to-date information about software packages and their dependencies during software installation.
### Step 2: Install Zsh

Run the following command to install Z Shell on Ubuntu:

```sh
sudo apt install zsh -y
```

The **`-y`** flag automatically answers **`yes`** to any prompts during the installation and provides consent for installing Zsh and its dependencies. Omit the flag if you want to review the installation.
### Step 3: Check Installation

After the installation finishes, check if it has been installed correctly by checking the program version. Run the following command:

```sh
zsh --version
```

![[line/assets/Pasted image 20240108084134.png]]
The output shows the current version installed on the system.
## Configure Zsh on Ubuntu

Configuring Zsh in Ubuntu allows you to personalize the shell environment, boost productivity with intelligent tab completion, and leverage the flexibility of Zsh scripting capabilities.

This section explores the steps to configure Zsh as your default shell in Ubuntu and introduces you to various customization options.
### Initial Configuration

Unlike Bash and other shells, Zsh requires initial configuration when you start it for the first time. To start Zsh, type the shell name in the terminal and press **Enter**:

```sh
zsh
```

The following screenshot shows the configuration options that Zsh offers on the first startup:

![[line/assets/Pasted image 20240108084545.png]]
- Press **1** to go to the main menu and configure each setting individually.
- Press **2** to populate the _.zshrc_ configuration file with the default parameters, which you can later change manually in the _.zshrc_ file.
- Press **0** to create an empty _.zshrc_ configuration file and configure everything from scratch.
- Press **q** to exit the configuration and start it again the next time you enter Zsh.

After you complete the setup, the changes are saved, and the Z Shell prompt appears. **The initial setup appears only the first time you run the shell**, but you can rerun the initial setup with the **`zsh-newuser-install`** command.

### Set Zsh as Default Shell

After installation, Zsh is not configured and is not set as the default shell. To set Zsh as your default shell, follow the steps below:

1. Check which shell is the default one in your system:
The output states the value of the **`$SHELL`** variable, which is the default shell.

```sh
echo $SHELL
```

![Checking the default shell in Linux.](https://phoenixnap.com/kb/wp-content/uploads/2023/07/see-default-shell-in-linux.png)


2. Use the chsh (change shell) command to change the default login shell. The following syntax lets you change the default shell with **`chsh`**:

```sh
chsh -s [path] [user]
```

- **`[path]`** specifies the path to the shell you want to use.
- **`[user]`** specifies the user for which you want to change the default shell. Not specifying the user changes the default shell for the current user.

If you are unsure of the shell path, utilize the which command to specify the Zsh path automatically. For example:

```sh
chsh -s $(which zsh)
```

Enter the root password when prompted and press **Enter**.

![Entering the root password for the Zsh path.](https://phoenixnap.com/kb/wp-content/uploads/2023/07/change-default-shell-in-linux.png)

The command changes the default shell to Zsh for the current user. To start using the Z Shell, log out of the terminal and log back in.

### Uninstall Zsh

If you decide to remove Zsh from your system and revert to the old shell, follow the steps below to uninstall it:

1. Purge the **`zsh`** package from the system by running the following command:

```sh
sudo apt --purge remove zsh
```

When prompted, type **`y`** and press **Enter** to confirm you want to remove Zsh.
Purging a package removes the package and deletes any associated configuration files and dependencies automatically installed with the package.

2. Change the default shell back to Bash (or any other you want):

```sh
chsh -s $(which bash)
```

3. Close the terminal and open a new session for the changes to take effect.