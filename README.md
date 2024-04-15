<h2 align="center"> ━━━━━━  △  ━━━━━━ </h2>
<div align="center">
   <p></p>
   <a href="https://discord.gg/linuxfr">
      <img alt="Discord server :3" src="https://discord.com/api/guilds/1058067015891431514/embed.png?style=banner4">
   </a>
   <br>
</div>
<p/>
<h2></h2>

<!-- INFORMATION -->
## :cat: <samp>INFORMATIONS</samp>

<img align="right" width="400" height="225" src="https://cdn.discordapp.com/attachments/1097223823935418538/1099059637023682650/neko.png?ex=662c058d&is=6619908d&hm=58681f2e73fe5be817f2c50a164a06458834246bb2d2d8bddc58f3a5f1140329&">

- **Window Manager:** [bspwm](https://github.com/baskerville/bspwm)
- **Terminal:** [kitty](https://github.com/kovidgoyal/kitty)
- **Shell:** [zsh](https://www.zsh.org/)
- **Compositor:** [picom](https://github.com/yshui/picom)
- **Editor:** [neovim](https://github.com/neovim/neovim)
- **Browser:** [librewolf](https://librewolf.net/)
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
CFG_GIT=https://github.com/kittygirlyy/.dotfiles.git

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

<h1 align="center">𓆩♡𓆪 𝑨𝑷𝑲'𝒔 𓆩♡𓆪</h1>

<table align="center">
  <tr><th>Name</th>                       <th></th></tr>
  <tr><td>X-Plore PRO</td>                <td><a href="https://github.com/kittygirlyy/.dotfiles/blob/main/android/apk/X-plore.apk">Link</a></td></tr>
  <tr><td>F-Droid</td>                    <td><a href="https://github.com/kittygirlyy/.dotfiles/blob/main/android/apk/F-Droid.apk">Link</a></td></tr>
  <tr><td>DuckDuckGo</td>                 <td><a href="https://github.com/kittygirlyy/.dotfiles/blob/main/android/apk/DuckDuckGo.apk">Link</a></td></tr>
</table>

<!-- NEKO -->
