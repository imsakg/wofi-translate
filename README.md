# Wofi translate

Simple wofi script for translation based on [translate shell](https://github.com/soimort/translate-shell)

## Demo

### Brief mode

Brief translation, provide simple translation with pronunciation audio.

![Demo1](./demo/demo1.gif)

### Verbose mode

Provide detail of specific translation

![Demo2](./demo/demo2.gif)

## Requirement

* wofi
* [translate shell](https://github.com/soimort/translate-shell)
* mplayer (without it you can't play the audio file)
* usleep
* awk
* sed
* tac

### Archlinux
``` bash
sudo pacman -S translate-shell wofi mplayer
```

## Install
### Download wofi-translate
``` bash
git clone https://github.com/imsakg/wofi-translate.git
cd woif-translate
```

### Configure environment variables
Edit `.bashrc`, add the following line.
``` bash
export PATH=~/wofi-translate:$PATH
```

### Usage

shell
``` bash
$ wofi_trans
$ wofi_trans brief
$ wofi_trans verbose
$ wofi_trans delete
```

Add key binding for i3-wm
``` plaintext
bindsym $mod+t exec wofi_trans
```
Add key binding for hyprland
``` plaintext
bind = SUPER SHIFT, T, exec, wofi_trans
```

### Configuration of wofi-translate

Open the file ``wofi_trans`` with your text editor.
Then make changes to these environment variables.

```bash
function Configs {
    # the default translation engine for translate-shell.
    export primary_translator="google"

    # the alternative translation engine for translate-shell. Once the primary engine malfunctioned, the secondary engine replace it.
    export secondary_translator="bing"

    # the file use to storing your translating history.
    export transHistory="$HOME/.wofi_trans"

    # Directory for cache audio files
    export transAudioCacheDir="$HOME/.wofi_trans_audio"

    # target language for translation
    export transTarget="en"

    # transArgs: Arguement for translate shell
    export transArgs="-b -speak"

    # display some debug information, run it in shell so you can see it
    export verbose="1"

    # auto refresh the content of each mode after every operation, this will cause the wofi flash(close and open)
    export auto_refresh="1"

    export version=1
}
```