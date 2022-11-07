# Windows-Initial-Setup-Script - Awesome muso

N�sleduje seznam u�ite�n�ch skript�, kter� �in� Windows po jejich �erstv� instalaci pou�iteln�j��mi. Odstra�uje v�echny
nesmysly, zbyte�nosti, reklamy, trackery a spoustu dal��ho (kdo zn�te skript od DASM, tak toto je sv�m zp�sobem jeho
pokra�ov�n�).

V dal��m kroku s pomoc� Chocolatey nainstaluje nejpou��van�j�� programy a utility. 

V�e spou�t�t z Powershell Windows, kter� je spu�t�n� p�es prav� tla��tko a "Spustit jako spr�vce".

```powershell
# Unrestrict execution of scripts in PowerShell
Set-ExecutionPolicy unrestricted

# St�hnut� Sophia script
irm script.sophi.app -useb | iex

# Sophia script - spu�t�n� skriptu 
.\Sophia.ps1

# Windows 10 - odinstalace zbyte�nost�, kter� v�choz� nastaven� skriptu nepobere (OneDrive,.Disney+, Spotify)
.\Sophia.ps1 -Functions "OneDrive -Uninstall"
Get-AppxPackage -Name *SpotifyAB.SpotifyMusic* -AllUsers | Remove-AppxPackage -AllUsers
Get-AppxPackage -Name *Disney.37853FC22B2CE* -AllUsers | Remove-AppxPackage -AllUsers

# Windows 11 - odinstalace zbyte�nost�, kter� v�choz� nastaven� skriptu nepobere (OneDrive,.Disney+, Spotify), Start menu doleva
.\Sophia.ps1 -Functions "OneDrive -Uninstall"
Get-AppxPackage -Name *SpotifyAB.SpotifyMusic* -AllUsers | Remove-AppxPackage -AllUsers
Get-AppxPackage -Name *Disney.37853FC22B2CE* -AllUsers | Remove-AppxPackage -AllUsers
 .\Sophia.ps1 -Functions "TaskbarAlignment -Left"
 .\Sophia.ps1 -Functions "RecycleBinDeleteConfirmation -Disable"

# Aktualizace modul� PowerShellGet, PowerShellManagement, PSReadLine
iwr https://raw.githubusercontent.com/farag2/Windows_Terminal/main/Install_Modules.ps1 -UseBasicParsing | iex 

# Instalace Chocolatey package manager
[System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
choco feature enable -n allowGlobalConfirmation
choco feature enable -n allowEmptyChecksums

# Instalace software p�es Chocolatey
choco install vlc 7zip googlechrome firefox opera keepassxc notepadplusplus winscp openvpn xnview
choco install telegram viber discord 
choco install totalcommander

# Add git and node to path
refreshenv

# U� NEPOU��V�M! ChrisTitusTech tool
#irm christitus.com/win | iex

# U� NEPOU��V�M! Optimizer tool
#Invoke-Webrequest (Invoke-RestMethod -uri https://api.github.com/repos/hellzerg/optimizer/releases/latest | select -ExpandProperty assets | select -expand browser_download_url) -OutFile Optimizer.exe; & .\Optimizer.exe

# (Optional) Edit and backup PowerShell command history
#code (Get-PSReadlineOption).HistorySavePath
```

Pro instalaci Windows Subsystem for Linux  https://github.com/musosoft/awesome-muso/blob/master/install-WSL.md

P�evzato a upraveno pro vlastn� pot�eby od Muso https://github.com/musosoft/awesome-muso
