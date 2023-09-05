
[<- Back to Start](https://github.com/Thirstums/Notes/blob/main/README.md)
# My Powershell Setup Guide

<span style="color:#F4B8E4">

## Preview
</span>

![Powershell](https://github.com/Thirstums/Notes/blob/main/Img/Powershell_Preview.png)

![Powershell vim](https://github.com/Thirstums/Notes/blob/main/Img/Powershell_vim_preview.png)


<span style="color:#BABBF1"> 

## Current Powershell Profile
</span>

<details>
  <summary>Open</summary>
  
```powershell
# Icons
Import-Module -Name Terminal-Icons

# PSReadline
Set-PSReadLineOption -EditMode Emacs
Set-PSReadlineOption -BellStyle None
Set-PSReadlineKeyHandler -Chord 'Ctrl+d' -Function DeleteChar
Set-PSReadLineOption -PredictionSource HistoryAndPlugin
Set-PSReadLineOption -PredictionViewStyle ListView

# Fzf
Import-Module PSFzf
Set-PsFzfOption -PSReadlineChordProvider 'Ctrl+f' -PSReadlineChordReverseHistory 'Ctrl+r'

# Prompt
Import-Module posh-git
Import-Module Terminal-Icons

# Load prompt config
function Get-ScriptDirectory { Split-Path $MyInvocation.ScriptName }
$PROMPT_CONFIG = Join-Path (Get-ScriptDirectory) 'thirstums.omp.json'
oh-my-posh init pwsh --config $PROMPT_CONFIG | Invoke-Expression


# Shutdown options

# Shutdown
function sd {
  shutdown /s
}

# Restart
function rs {
  shutdown /r
}

# Open Applications

# Open Discord
function discord {
   Start-Process 'C:\Users\janis\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Discord Inc\Discord.lnk'
}

# Open Microsoft Edge
function edge {
   Start-Process 'C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Microsoft Edge.lnk'
}

#Open File Expolorer (current location)
function e {
   ii .
}

# Open Taskmanager 
function tm {
   taskmgr
}

#Kill Tasks

function kDiscord {
   taskkill /IM Discord.exe /F
}

function kCode {
   taskkill /IM Code.exe /F
}

# Alias
Set-Alias vim nvim
Set-Alias ll ls
Set-Alias g git
Set-Alias grep findstr
Set-Alias tig 'C:\Program Files\Git\usr\bin\tig.exe'
Set-Alias less 'C:\Program Files\Git\usr\bin\less.exe'

# Utilities
function which ($command) {
  Get-Command -Name $command -ErrorAction SilentlyContinue |
    Select-Object -ExpandProperty Path -ErrorAction SilentlyContinue
}

```

</details>

<span style="color:#8CAAEE"> 

## Current oh-my-posh Theme
</span>

<details>
  <summary>Open</summary>

```json
{
  "$schema": "https://raw.githubusercontent.com/JanDeDobbeleer/oh-my-posh/main/themes/schema.json",
  "palette": {
    "os": "#ACB0BE",
    "closer": "p:os",
    "pink": "#F4B8E4",
    "lavender": "#BABBF1",
    "blue": "#8CAAEE"
  },
  "blocks": [
    {
      "alignment": "left",
      "segments": [
        {
          "foreground": "p:os",
          "style": "plain",
          "template": "{{.Icon}} ",
          "type": "os"
        },
        {
          "foreground": "p:blue",
          "style": "plain",
          "template": "{{ .UserName }}@{{ .HostName }} ",
          "type": "session"
        },
        {
          "foreground": "p:pink",
          "properties": {
            "folder_icon": "..\ue5fe..",
            "home_icon": "~",
            "style": "agnoster_short"
          },
          "style": "plain",
          "template": "{{ .Path }} ",
          "type": "path"
        },
        {
          "foreground": "p:lavender",
          "properties": {
            "branch_icon": "\ue725 ",
            "cherry_pick_icon": "\ue29b ",
            "commit_icon": "\uf417 ",
            "fetch_status": false,
            "fetch_upstream_icon": false,
            "merge_icon": "\ue727 ",
            "no_commits_icon": "\uf0c3 ",
            "rebase_icon": "\ue728 ",
            "revert_icon": "\uf0e2 ",
            "tag_icon": "\uf412 "
          },
          "template": "{{ .HEAD }} ",
          "style": "plain",
          "type": "git"
        },
        {
          "style": "plain",
          "foreground": "p:closer",
          "template": "\uf105",
          "type": "text"
        }
      ],
      "type": "prompt"
    },
    {
      "alignment": "right",
      "segments": [
        {
          "type": "time",
          "style": "plain",
          "foreground": "#F4B8E4",
          "properties": {
            "time_format": "15:04:05"
          }
        }
      ],
      "type": "prompt"
    },
    {
      "alignment": "left",
      "newline": true,
      "segments": [
        {
          "foreground": "#F4B8E4",
          "style": "plain",
          "template": " ~ ",
          "type": "text"
        }
      ],
      "type": "prompt"
    }
  ],
  "final_space": true,
  "version": 2
}
```

</details>

## Terminal install win 10/11
- [Terminal](https://github.com/microsoft/terminal)

```powershell
winget install --id Microsoft.WindowsTerminal -e
```


## Powershell Theme
### Enable Acrylic material in Terminal appearence settings:

![Acrylic Material](https://github.com/Thirstums/Notes/blob/main/Img/PowershellEnableAcrylicMaterial.png)


Open Json file and add this theme belove the Vintage theme:

```Json 
{
            "background": "#001B26",
            "black": "#000000",
            "blue": "#779ECB",
            "brightBlack": "#F2C6DE",
            "brightBlue": "#9E9EEB",
            "brightCyan": "#8EC4F0",
            "brightGreen": "#C9E4DE",
            "brightPurple": "#FF00FF",
            "brightRed": "#FF71C0",
            "brightWhite": "#EAC7FF",
            "brightYellow": "#F2C6DE",
            "cursorColor": "#FFFFFF",
            "cyan": "#008080",
            "foreground": "#C0C0C0",
            "green": "#B0E9D5",
            "name": "VintageV2",
            "purple": "#966FD6",
            "red": "#FF1391",
            "selectionBackground": "#F2C6DE",
            "white": "#C0C0C0",
            "yellow": "#F2C6DE"
        }
```

## Scoop installation

[Scoop](https://scoop.sh/)

```Powershell
iwr -useb get.scoop.sh | iex
```
## Git for windows Installation

[Git For Windows](https://gitforwindows.org/)

```Powershell
winget install -e --id Git.Git
```

## Install Neovim

[Neovim](https://neovim.io/)

```Powershell
scoop install neovim gcc
```
enter Neovim
```powershell
nvim
```
exit Neovim
```powershell
:qa!
```


### setup New Pwsh Profile

create new directory
```powershell
mkdir .config\powershell
```
Change Directory
```powershell
cd .config\powershell
```

create & edit new Pwsh Profile
```powershell
vim .config\powershell\user_profile.ps1
```

#### Change powershell profile location (*redirect in default profile file*)

open in vim
```powershell
nvim $PROFILE.CurrentUserCurrentHost
```
Create Variable
```powershell
$env:USERPROFILE\.config\powershell\user_profile.ps1
```
 to safe
```powershell
:wqa
```

## Oh my Posh Installation

[OhMyPosh](https://ohmyposh.dev/docs/installation/windows)

```powershell
Install-Module posh-git -Scope CurrentUser -Force
```

```powershell
scoop install https://github.com/JanDeDobbeleer/oh-my-posh/releases/latest/download/oh-my-posh.json
```

Preview template themes

```powershell
Get-PoshThemes
```

Add a Theme (your own or a template)

```powershell
oh-my-posh init pwsh --config yourPrompt.omp.json | Invoke-Expression
```

Install nerd font with oh my posh (Optional)

```powershell
oh-my-posh font install
```

## Install Terminal Icons

In order for Terminal Icons to work you need to install a Nerd font

- [Terminal-Icons](https://github.com/devblackops/Terminal-Icons)
- [NerdFonts](https://www.nerdfonts.com/)

```powershell
Install-Module -Name Terminal-Icons -Repository PSGallery -Force
```

Add this Import to your Powershell Profile
```Powershell
Import-Module Terminal-Icons
```

## Install z Directory Jumper

```Powershell
Install-Module -Name z -Force
```
for example after using the ```cd .\.config\powershell``` A few times
```powershell
z powershell
```
will go to ```.\.config\powershell```


z learns through your ```cd``` histroy and will create shortcuts for you over time

## Install PS ReadLine

```powershell
Install-Module -Name PSReadLine -AllowPrerelease -Scope CurrentUser -Force -SkipPublisherCheck
```

```powershell
Set-PSReadLineOption -PredictionSource History
```

```powershell
Set-PSReadLineOption -PredictionViewStyle ListView
```

## Install PSFzf


```powershell
scoop install fzf
```

```powershell
Install-Module -Name PSFzf -Scope CurrentUser -Force
```

## Install Powertoys
- [PowerToys](https://learn.microsoft.com/en-us/windows/powertoys/install)
```
winget install Microsoft.PowerToys --source winget
```

## Install Rainmeter

- [Rainmeter](https://docs.rainmeter.net/manual/installing-rainmeter/)
```
winget install Rainmeter
```

# Powershell useful commands

Kills any running Process

```powershell
taskkill /IM application.exe /F
```

