# Windows-Initial-Setup-Script - Awesome muso

Následuje seznam užiteèných skriptù, které èiní Windows po jejich èerstvé instalaci použitelnìjšími. Odstraòuje všechny
nesmysly, zbyteènosti, reklamy, trackery a spoustu dalšího (kdo znáte skript od DASM, tak toto je svým zpùsobem jeho
pokraèování).

V dalším kroku s pomocí Chocolatey nainstaluje nejpoužívanìjší programy a utility. 

Vše spouštìt z Powershell Windows, který je spuštìný pøes pravé tlaèítko a "Spustit jako správce".

```powershell
# Unrestrict execution of scripts in PowerShell
Set-ExecutionPolicy unrestricted


# Sophia script - po stažení spustit SophiApp.exe
irm script.sophi.app | iex

# Chocolatey package manager
[System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
choco feature enable -n allowGlobalConfirmation
choco feature enable -n allowEmptyChecksums

# Install software
choco install vlc 7zip googlechrome firefox opera keepassxc notepadplusplus totalcommander telegram viber discord winscp openvpn

# Add git and node to path
refreshenv

# UŽ NEPOUŽÍVÁM! ChrisTitusTech tool
#irm christitus.com/win | iex

# UŽ NEPOUŽÍVÁM! Optimizer tool
#Invoke-Webrequest (Invoke-RestMethod -uri https://api.github.com/repos/hellzerg/optimizer/releases/latest | select -ExpandProperty assets | select -expand browser_download_url) -OutFile Optimizer.exe; & .\Optimizer.exe

# (Optional) Edit and backup PowerShell command history
#code (Get-PSReadlineOption).HistorySavePath
```

Pro instalaci Windows Subsystem for Linux  https://github.com/musosoft/awesome-muso/blob/master/install-WSL.md

Pøevzato a upraveno pro vlastní potøeby od Muso https://github.com/musosoft/awesome-muso
