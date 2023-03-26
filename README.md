<h2 align="center"> ━━━━━━  △  ━━━━━━ </h2>
<div align="center">
   <p></p>
   <a href="https://discord.gg/linuxfr">
      <img alt="Discord server" src="https://discord.com/api/guilds/1058067015891431514/embed.png?style=banner4">
   </a>
   <br>
</div>
<p/>
<h2></h2>

<!-- INFORMATION -->
## :cat: <samp>INFORMATIONS</samp>

<img align="right" width="400" height="225" src="https://cdn.discordapp.com/attachments/1050059938233319465/1057402587898458233/image.png">

- **Window Manager:** [bspwm](https://github.com/baskerville/bspwm)
- **Terminal:** [kitty](https://github.com/kovidgoyal/kitty)
- **Shell:** [zsh](https://www.zsh.org/)
- **Compositor:** [picom](https://github.com/yshui/picom)
- **Editor:** [neovim](https://github.com/neovim/neovim)
- **Browser:** [firefox](https://www.mozilla.org/en-US/firefox)
- **Notification Daemon:** [dunst](https://github.com/dunst-project/dunst)
- **Development Environnement:** [VSCodium](https://github.com/VSCodium/vscodium)


<!-- MAKE INSTALLATION EASIER -->
## 🌿 <samp>MAKE INSTALLATION EASIER</samp>

```bash
#!/bin/sh

# ##################################################### #
#                                                       #
#                   Download cfg :3                     #
#                     DO NOT RUN AS SUDO                #
# ##################################################### #

ERRCODE=12
CFG_GIT=https://github.com/n3k0girl/.dotfiles.git

##   Checking if .dotfiles   ##

ls .dotfiles 2> err
if [ "$?" == 0 ]
then
    rm -rf .dotfiles
    echo "The repository folder were removed"
fi

##   Download packages   ##


sudo pacman -Sy kitty sxhkd bspwm zsh polybar picom nitrogen curl git

if [ "$?" != 0 ]
then
    echo "Error while downloading packages"
    exit $ERRCODE
fi

##   Download cfg   ##

git clone $CFG_GIT

if [ "$?" != 0 ]
then
    echo "Error while cloning remote repository" $CFG_GIT
    exit $ERRCODE
fi

##   Copying cfg files   ##

CFG_DIR=(".dotfiles/linux/kitty/kitty.conf" ".dotfiles/linux/sxhkd/sxhkdrc" ".dotfiles/linux/bspwm/bspwmrc" ".dotfiles/linux/polybar/*" ".dotfiles/linux/dunst/dunstrc" ".dotfiles/linux/picom/picom.conf" ".dotfiles/linux/.xprofile")
DIRNAME=("kitty" "sxhkd" "bspwm" "polybar" "dunst" "picom" ".xprofile")
LEN=${#DIRNAME[@]}

for (( i=0; i<=$LEN; i++ ))
do
    if [ "${DIRNAME[i]}" == ".xprofile" ]
    then
        mv ${CFG_DIR[i]} ~/${DIRNAME[i]} 2> err
        echo "Done !"
        exit 100
    fi
  
    mkdir ~/.config/${DIRNAME[i]} 2> err
    if [ "$?" != 0 ]
    then
        echo ~/.config/${DIRNAME[i]} "is already here..."
    fi

    mv ${CFG_DIR[i]} ~/.config/${DIRNAME[i]}/ 2> err
done
```
