# Guia rápido

## :white_check_mark: Link para outros sites com dicas rápidas:

* https://cheatsheets.zip/
* https://devhints.io/ 
* https://learnxinyminutes.com/
* https://github.com/gto76/python-cheatsheet
* https://guialinux.uniriotec.br
* https://quickref.me/
* https://yoksel.github.io/flex-cheatsheet/
* https://git.uwaterloo.ca/-/snippets/117
* https://gist.github.com/beyonddream/a43e067db6336b03a2c4fc5da59ba507
* https://crontab.guru/ 

## :white_check_mark: Windows vars and tips

| Variable          | Description                                          |
|------------------|------------------------------------------------------|
| `%APPDATA%`      | Path to the current user's Application Data folder   |
| `%TEMP%`         | Path to the temporary folder for the current user    |
| `%USERPROFILE%`  | Path to the current user's profile folder           |
| `%PROGRAMFILES%` | Path to the Program Files folder                     |
| `%SYSTEMROOT%`   | Path to the Windows installation directory           |
| `%USERNAME%`     | Current user's username                              |
| `%WINDIR%`       | Path to the Windows directory                        |
| `%HOMEPATH%`     | Path to the current user's home folder              |
| `%LOCALAPPDATA%` | Path to the current user's local AppData folder     |
| `shell:startup`  | AppData\Roaming/Microsoft/Windows/Start Menu/Programs/Startup folder |

| Shortcut          | Program                                             |
|-------------------|-----------------------------------------------------|
| `control`         | Control Panel                                       |
| `sysdm.cpl`       | System Properties                                   |
| `ncpa.cpl`        | Network Connections                                 |
| `appwiz.cpl`      | Programs and Features                              |
| `desk.cpl`        | Display Properties                                  |
| `firewall.cpl`    | Windows Firewall                                    |
| `inetcpl.cpl`     | Internet Options                                    |
| `timedate.cpl`    | Date and Time                                       |
| `mmsys.cpl`       | Sound                                               |
| `powercfg.cpl`    | Power Options                                       |
| `devmgmt.msc`     | Device Manager                                      |
| `compmgmt.msc`    | Computer Management                                 |
| `services.msc`    | Services                                            |
| `taskmgr`         | Task Manager                                        |




## :white_check_mark: Linux

### Listar top 10 comandos com maior uso de cpu

```
ps -A --format=pcpu,args --sort=-pcpu | head -n 11 | cut -c 1-100
```

### Serviços (exemplos de comandos)

```
sudo service --status-all
sudo service smbd status
sudo service smbd start
sudo service smbd stop

sudo systemctl list-units | grep smbd.service
sudo systemctl list-units | grep docker.service
sudo systemctl start docker.service
sudo systemctl stop docker.service
sudo systemctl enable docker.service
sudo systemctl disable docker.service
sudo systemctl status docker.service
```

### SCP (copy files over ssh )

Copy files from server to local:
```
scp user@192.168.1.55:/folder/*.* /local/folder/
```

Copy files from local to server:
```
scp /local/folder/*.* user@192.168.1.55:/folder/ 
```
In this example, the server IP is 192.168.1.55

### CHMOD

Add read/write permissions recursivelly for all groups in all files/folders:

```
sudo chmod -R a+rw /path/to/folder
```

## :white_check_mark: Sintaxes de comandos nas linguagens que utilizo

| Comando           | C#                      | Node                    | Python                  |
|------------------|-------------------------|-------------------------|-------------------------|
| String interpolation | `$"my name is {name}"` | `` `my name is ${name}` `` | `f'my name is {name}'` (new)<br> `"my name is {}".format(name)` |

## :white_check_mark: Comandos de Terminal em Windows e Linux


| ENV vars         | Mac                     | Linux                   | PowerShell             |
|------------------|------------------------|-------------------------|------------------------|
| Show all         | `echo $ENV`            | `printenv`              | `dir env:`             |
| Show one         | `echo $ENV_VAR`        | `echo $ENV_VAR`         | `dir env:JAVA_HOME`    |
| Add new          | `export NEW_VAR=value` | `export NEW_VAR=value`  | `$env:NEW_VAR = "value"` |
 
 
| Comando          | Linux / Mac            | cmd or Powershell       |
|------------------|------------------------|-------------------------|
| AND operator     | `&&`                   | `&&`                    |
| Line Break       | `\`                    | `^` (cmd), \` (ps)      |
| Exibir caminho   | `which`                | `where`                 |
| Localizar arquivo| `find ./ -iname "*teste*"` | `dir -Recurse teste.txt` |
| Testar uma porta | `Telnet 192.168.1.55 80`<br>`nc -vz 192.168.1.55 80` | `Telnet 192.168.1.55 80` |
| Command substitution | `$(pwd)` or `` `pwd` `` | não tem                |
| Flush DNS        | `sudo killall -HUP mDNSResponder`<br>`sudo /etc/init.d/networking restart` | `ipconfig /flushdns` |
| Watch file       | `tail -f /var/log/syslog` | `Get-Content -Path "file.txt" -Wait` |
| remove all       | `rm -rf folder`        | `Remove-Item -Force -Recurse folder` |
| create file      | `touch file.txt`       | `New-Item file.txt`     |

## :white_check_mark: Git (exemplos)

### Stash

| Objetivo         | Comando                                              |
|------------------|-----------------------------------------------------|
| Stash one file   | `git stash push -m "message" -- test.txt`           |
| Stash untracked  | `git stash push -m "message" -u`                    |
| Apply staged too | `git stash apply --index`                           |
| Apply specific   | `git stash apply stash@{0}`                         |

## :white_check_mark: Docker (exemplos)

### Imagens

| Objetivo         | Comando                                              |
|------------------|-----------------------------------------------------|
| Baixar imagem    | `docker pull mcr.microsoft.com/dotnet/core/runtime:3.1` |
| Listar imagens   | `docker image list --all`                           |
| Remover imagem   | `docker image rm mcr.microsoft.com/dotnet/core/runtime:3.1` |
| Remover unused   | `docker image prune --all`                          |

### Containers

| Objetivo         | Comando                                              |
|------------------|-----------------------------------------------------|
| Criar container  | `docker container create -it --name 31 mcr.microsoft.com/core/runtime:3.1` |
| Listar containers| `docker container list --all`                        |
| Iniciar container| `docker container start 31`                          |
| Copiar arquivos  | `docker cp bin/. 31:home/bin`                       |
| Conectar container| `docker container exec -it 31 /bin/bash`            |
| Acompanhar logs  | `docker logs --follow 31`                           |
| Parar container  | `docker container stop 31`                          |
| Remover container| `docker container rm 31`                            |
| Remove stopped   | `docker container prune`                            |
| Limpar tudo     | `docker system prune --all`                         |

### Docker compose

| Objetivo         | Comando                                              |
|------------------|-----------------------------------------------------|
| Docker compose "iterativo" | `sudo docker-compose run --rm service1` |

Exemplo de docker-compose.yml "iterativo":
```yml
version: "3"
services:
  service1:
    image: mcr.microsoft.com//core/runtime:3.1
    stdin_open: true
    tty: true
    command: "/bin/bash"
```
### Docker (more)

```
docker system prune --all
docker volume prune 
``` 

## :white_check_mark: dotnet core
```bash
dotnet publish --configuration release --runtime linux-x64
dotnet publish --configuration release --runtime osx-x64 --self-contained true -p:PublishSingleFile=true
dotnet publish --configuration Release --runtime win-x64 --self-contained -p:PublishSingleFile=true -p:PublishTrimmed=true
dotnet nuget locals all --clear
```

## :white_check_mark: Configuração do VS Code

Instalar os plugins:

* EditorConfig for VS Code
* ESLint
* vscode-icons

Configurar o settings.json (CTRL + SHIFT + P) - Preferences - Open Settings:
```json
{
    "editor.fontFamily": "'Source code pro', Consolas, 'Courier New', monospace",
    "editor.fontSize": 14,
    "window.zoomLevel": 0,
    "workbench.startupEditor": "newUntitledFile",
    "workbench.iconTheme": "vscode-icons",
    "vsicons.presets.foldersAllDefaultIcon": true,
    "terminal.integrated.shell.windows": "C:\\WINDOWS\\System32\\cmd.exe",
    "editor.codeActionsOnSave": {
        "source.fixAll.eslint": true
    },
    "workbench.colorCustomizations": {
        "tab.activeBorderTop": "#ff0000"
    }  
}
```
## :white_check_mark: Abrir VS Code no MACOS pelo prompt:

* Open the Command Palette (Ctrl+Shift+P) and type 'shell command' to find the Shell Command: 
* Install 'code' command in PATH command.

## :white_check_mark: Temp (catalogar depois...)

Subnet CIDR examples:

```
+--------+-----------------+
| CIDR   | Subnet Mask     |
+--------+-----------------+
| /32    | 255.255.255.255 |
| /24    | 255.255.255.0   |
| /16    | 255.255.0.0     |
| /8     | 255.0.0.0       |
+--------+-----------------+
```

**Atalhos do Windows**:

- Network connections => Win+R ncpa.cpl
- [more..](https://www.itechtics.com/control-panel-applets-cpl/).
- more...
- etc...

Tirar o "verdão" do background da exibição dos diretórios no comando `ls`. <br>
Colocar isso no `.bashrc` da pasta `home` do usuário.
```
LS_COLORS='ow=01;36;40'
export LS_COLORS
```
<br><br>

CTRL + D no Visual Studio igual ao Visual Studio Code:
Tools => Options => Keyboard => Show Command containing string: 
```
Edit.InsertNextMatchingCaret
Edit.Duplicate
```
<br><br>

ssh no git:  
```
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

Fonte Source Code PRO
https://fonts.google.com/specimen/Source+Code+Pro
<br><br>

Instalar Java runtime 8 no MAC (pra usar com o VSTABI):
https://www.java.com/en/download/mac_download.jsp
<br><br>

Instalar o Java Development Kit 8 no MAC (pra desenvolver com o Eclipse):
https://www.oracle.com/java/technologies/javase/javase-jdk8-downloads.html
<br><br>

Link direto para o MAC OSX Mojave:
https://itunes.apple.com/us/app/macos-mojave/id1398502828?ls=1&mt=12  
  
Muito bom:
https://loading.io/css/
  
trocar cor da janela do windows não ativado (chipa Microsoft!!!):  
https://superuser.com/questions/1245923/registry-keys-to-change-personalization-settings  

remove windows 10 watermark
https://www.youtube.com/watch?v=X-E7syOcPEE  
  
https://coderwall.com/p/7smjkq/multiple-ssh-keys-for-different-accounts-on-github-or-gitlab  

find ./* | xargs xattr -r -d com.apple.quarantine


**Dica do Akita**

As Administrator!!!!

```PowerShell
wmic diskdrive list brief
```
```PowerShell
wsl --mount \\.\PHYSICALDRIVE1
```

```
echo $env:JAVA_HOME
```

```
dotnet nuget locals all --clear
```

The root account is disabled by default in Ubuntu, so there is no root password, that's why su fails with an authentication error.

# LSP shortcuts

| Command              | Visual Studio          | VS Code              | LazyVim         | Rider                   |
|----------------------|------------------------|----------------------|-----------------|-------------------------|
| Info (Hover)         | `K`                    | `K`                  | `K`             | `????????`              |
| Go to Definition     | `gd`                   | `gd`                 | `gd`            | `gd`                    |
| Go to Implementation | `gI`                   | `gI`                 | `gI`            | `gI`                    |
| Go to References     | `gr`                   | `gr`                 | `gr`            | `gr`                    |
| Navigate Back        | `<C-o>`                | `<C-o>`              | `<C-o>`         | `<C-o>`                 |
| Navigate Forward     | `<C-i>`                | `<C-i>`              | `<C-i>`         | `<C-i>`                 |
| Open Terminal        | `` Ctrl + ` ``         | `` Ctrl + ` ``       | `<C-/>`         | `?????????`             |
| Signature help       | `gK`                   | `gK`                 | `gK`            | `gK`                    |
| Rename Symbol        | `Ctrl + R, Ctrl + R`   | `F2`                 | `<leader>cr`    | `Shift + F6`            |
| Refactoring          | `Ctrl + R, Ctrl + R`   | `Ctrl + Shift + R`   | `<leader>ca`    | `Ctrl + Alt + Shift + T`|
| Format Document      | `Ctrl + K, Ctrl + D`   | `Shift + Alt + F`    | `<leader>cf`    | `Ctrl + Alt + L`        |
| Quick Fix            | `Ctrl + .`             | `Ctrl + .`           | `<leader>ca`    | `Alt + Enter`           |



Use sudo to become root:
```
sudo -i 
```
