-----------------------------INSTALL ARCH_LINUX---------------------------------

#1 Install Arch
- Follow this website instructions: https://linuxiac.com/arch-linux-install/

#2 Install vim and set up

    sudo pacman -S vim

-create ".vimrc" file with code: 

    syntax on               #enable syntax
    :set number             #show number line
    :colorscheme pablo      #set theme

#3 Install ZSH and set up

-install and set to default shell

    sudo pacman -S zsh
    sudo chsh -s $(which zsh)
    
-config zsh
+ install ohmyzsh:

      sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"

+ change theme: find and edit line ZSH_THEME="YOUR_THEME" in .zshrc file, with YOUR_THEME refer here https://github.com/ohmyzsh/ohmyzsh/wiki/themes

      ZSH_THEME="YOUR_THEME"
 

- install plugin autosuggestion, syntax highlighting, fzf:

        git clone https://github.com/zsh-users/zsh-autosuggestions.git $ZSH_CUSTOM/plugins/zsh-autosuggestions

        git clone https://github.com/zsh-users/zsh-syntax-highlighting.git $ZSH_CUSTOM/plugins/zsh-syntax-highlighting
        
        git clone --depth 1 https://github.com/junegunn/fzf.git ~/.fzf
        ~/.fzf/install
  
- add plugin: find and edit again for the same bellow in .zshrc file
  
        plugins=(git zsh-autosuggestions zsh-syntax-highlighting)
        
            
-----------------------------INSTALL_BSPWM-----------------------------------------


#1 Install require package

    sudo pacman -Syy
    sudo pacman -S xf86-video-intel xorg xorg-xinit bspwm sxhkd dmenu nitrogen picom xfce4-terminal chromium arandr alsa-utils

#2 Coppy file to .config directory

    install -Dm755 /usr/share/doc/bspwm/examples/bspwmrc ~/.config/bspwm/bspwmrc
    install -Dm644 /usr/share/doc/bspwm/examples/sxhkdrc ~/.config/sxhkd/sxhkdrc
    
#3 Edit .sxhkdrc file: change to xfce4-terminal

    # terminal emulator
    super + Return
            xfce4-terminal
           
#4 Create .xinitrc file in $HOME directory with content:
        
    xsetroot -cursor_name left_ptr
    picom -f &
    exec bspwm
        
#5 Comment in picom.conf file:
    
    #vsync = true
    
#6 Run bspwm
        
    startx
 
#7 install and set wallpapper: watch and follow instructions like video

https://www.youtube.com/watch?v=PLBm0C5Gv58&t=923s

-view 10:45 - 15:45

+install wallpapper

+arandr

+nitrogen

#8 auto run bspwm

-create z.profile file with content:
        
        if [ -z "${DISPLAY}" ] && [ "${XDG_VTNR}" -eq 1 ]; then
          exec startx
        fi
