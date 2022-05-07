# Windows-Initial-Setup-Script - Awesome muso

N�sleduje seznam u�ite�n�ch skript�, kter� �in� Windows po jejich �erstv� instalaci pou�iteln�j��mi. Odstra�uje v�echny
nesmysly, zbyte�nosti, reklamy, trackery a spoustu dal��ho (kdo zn�te skript od DASM, tak toto je sv�m zp�sobem jeho
pokra�ov�n�).

V dal��m kroku s pomoc� Chocolatey nainstaluje nejpou��van�j�� programy a utility. 

V�e spou�t�t z P��kazov� ��dky Windows, kter� je spu�t�n� p�es prav� tla��tko a "Spustit jako spr�vce".

```powershell
# Unrestrict execution of scripts in PowerShell
Set-ExecutionPolicy unrestricted

# ChrisTitusTech tool 
iwr -useb https://git.io/JJ8R4 | iex

# Sophia script
irm script.sophi.app | iex

# Optimizer tool
Invoke-Webrequest (Invoke-RestMethod -uri https://api.github.com/repos/hellzerg/optimizer/releases/latest | select -ExpandProperty assets | select -expand browser_download_url) -OutFile Optimizer.exe; & .\Optimizer.exe

# Chocolatey package manager
[System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
choco feature enable -n allowGlobalConfirmation
choco feature enable -n allowEmptyChecksums

# Install software
choco install vlc 7zip googlechrome firefox opera keepassxc notepadplusplus totalcommander telegram viber discord winscp openvpn

# Add git and node to path
refreshenv

# (Optional) Edit and backup PowerShell command history
code (Get-PSReadlineOption).HistorySavePath
```

Pro instalaci Windows Subsystem for Linux  https://github.com/musosoft/awesome-muso/blob/master/install-WSL.md

P�evzato a upraveno pro vlastn� pot�eby od Muso https://github.com/musosoft/awesome-muso
