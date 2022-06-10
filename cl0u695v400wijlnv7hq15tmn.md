## Using Holberton's Betty Linter for C on Emacs.

# HABITS
Habits can be very powerful. You already know that. You also know that breaking bad habits can take quite the effort. Knowing these, what price would you put on a tool that helps you cultivate the right habit easily?

*That's the price of this post. I know, a bold claim, but read on.*

Linters generally ensure your code conforms to a set standard. The goals of these standards are **maintainability and readability**. These are not just professional ethics, they are about saving you and any one who's going to use your code from nightmares.

If complying with these standards were a game chess, then having Holberton's Betty linter would be like having Magnus Carlsen as your personal coach. This article isn't just to get you to run  `betty <filename>` after you're done coding to see if you're compliant. It helps you set up Betty so she checks *line by line as you code* so you have one less thing to worry about. It is going to help you build the right habits from the start or help you break bad ones you already have.

Along the line, I also explain the following:
1. Basic commands in emacs.
2. How to add the MELPA repository to your emacs
3. How to install a package in emacs.

# Getting started...
The assumption is that you are using Ubuntu or any other debian derivative and you have emacs 24 or any recent version installed (other flavours of emacs do not work). You can install emacs from your terminal with this command:

```sudo apt install emacs```

## Customizing Emacs
Next, you want to install the *flycheck* package. The package is only available on the MELPA repository so you'll have to add that to your available packages if you don't already have it. To get started, note that *C* means the *ctrl* key and *M* means the *alt* key. So *C-x* means *ctrl + x*.

Now, on emacs, type:
> C-x d

After hitting *Enter*, it opens up your directories and files. Navigate to your *.emacs* file and click on it. Next, you want to add the following code to it (Useful tip: the command to paste in emacs is *C-y*):

```
(require 'package)
(add-to-list 'package-archives
	     '("melpa-stable" . "https://stable.melpa.org/packages/") t)
(package-initialize)
``` 

What this does is tell emacs to make the packages in MELPA to available to you.

Type the following next:
> C-x s         (This saves your change. Remember to click 'y' at the prompt).

> C-x C-x     (This exits emacs.)

Open emacs again and type:
> M-x list-packages

You should find something like this:

![Screenshot from 2022-03-16 22-41-59.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1647467115458/2wb6HBzWC.png)

This displays a list of all the packages available to you. You'll find that it also includes ones from MELPA.
Move down to *flycheck*. Type
> I (This tells emacs you want to install that package. The letter *I* should appear)

> x (This installs the selected package. Remember to follow the prompt)

Once this is done, you can exit emacs.

## Setting up Betty
You first need to clone the Betty-on-Emacs repository from GitHub to your computer. Run the following code from your terminal one line at a time.

```
git clone https://github.com/havk64/Betty-on-Emacs.git

cd Betty-on-Emacs

./install.sh
```
After this, open emacs again, go to your *.emacs* file and type the following lines

```
(load "~/.emacs.d/private/Betty/betty-style")
(add-to-list 'flycheck-checkers 'betty-style)

(setq flycheck-gcc-pedantic t)
(setq flycheck-gcc-warnings '("all" "extra" "error"))

(add-hook 'after-init-hook #'global-flycheck-mode)

(setq c-default-style "bsd"
      c-basic-offset 8
      tab-width 8
      indent-tabs-mode t)

(require 'whitespace)
(setq whitespace-style '(face empty lines-tail trailing))
(global-whitespace-mode t)

(setq column-number-mode t)
``` 
Save and exit emacs

# Rounding up...
At this point, your emacs if fully setup to check with Betty as you code. To read more about what the Betty coding style is, please check [here](https://github.com/holbertonschool/Betty/wiki).

You might find Betty a hassle at first, but as you continue with this, you'll get used to her. Remember, you are trying to build the right habit.

Thank you for reading, see you soon!