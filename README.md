# Guia rápido

## :white_check_mark: Link para outros sites com dicas rápidas:

* https://devhints.io/ 
* https://learnxinyminutes.com/
* https://github.com/gto76/python-cheatsheet
* https://guialinux.uniriotec.br
* https://quickref.me/
* https://yoksel.github.io/flex-cheatsheet/
* https://git.uwaterloo.ca/-/snippets/117
* https://gist.github.com/beyonddream/a43e067db6336b03a2c4fc5da59ba507  

## :white_check_mark: Windows vars and tips

| Variable        | Description                                             |
|-----------------|---------------------------------------------------------|
| `%APPDATA%`     | Path to the current user's Application Data folder      |
| `%TEMP%`        | Path to the temporary folder for the current user       |
| `%USERPROFILE%` | Path to the current user's profile folder               |
| `%PROGRAMFILES%`| Path to the Program Files folder                        |
| `%SYSTEMROOT%`  | Path to the Windows installation directory              |
| `%USERNAME%`    | Current user's username                                 |
| `%WINDIR%`      | Path to the Windows directory                           |
| `%HOMEPATH%`    | Path to the current user's home folder                  |
| `%LOCALAPPDATA%`| Path to the current user's local AppData folder         |
| `shell:startup` | AppData\Roaming/Microsoft/Windows/Start Menu/Programs/Startup folder |

| Shortcut                     | Program                                     |
|------------------------------|---------------------------------------------|
| `control`                    | Control Panel                               |
| `sysdm.cpl`                  | System Properties                           |
| `ncpa.cpl`                   | Network Connections                         |
| `appwiz.cpl`                 | Programs and Features                       |
| `desk.cpl`                   | Display Properties                          |
| `firewall.cpl`               | Windows Firewall                            |
| `inetcpl.cpl`                | Internet Options                            |
| `timedate.cpl`               | Date and Time                               |
| `mmsys.cpl`                  | Sound                                       |
| `powercfg.cpl`               | Power Options                               |
| `devmgmt.msc`                | Device Manager                              |
| `compmgmt.msc`               | Computer Management                         |
| `services.msc`               | Services                                    |
| `taskmgr`                    | Task Manager                                |




## :white_check_mark: Linux

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

## :white_check_mark: Sintaxes de comandos nas linguagens que utilizo

| Comando | C# | Node | Python
| ------- | ----- | ------- | ------- |
| String interpolation | `$"my name is {name}"` | `` `my name is ${name}` ``  | `f'my name is {name}'` (new)<br> `"my name is {}".format(name)` |

## :white_check_mark: Comandos de Terminal em Windows e Linux

| Comando | Linux / Mac | cmd or Powershell |
| ------- | ----- | ------- |
| AND operator (vários comandos) | `&&` | `&&` |
| Line Break (útil para linhas muito grandes) | `\` | `^` para cmd e 'backtick' para powershell |
| Exibir caminho de app no path | `which` | `where` |
| Localizar arquivo | `find ./ -iname "*teste*"` | `dir /s teste.txt` |
| Variáveis de ambiente | `env` <br> `export VAR1=teste` <br> `echo $VAR1` | `set` <br> `set VAR1=teste` <br> `echo %VAR1%` <br> `Get-ChildItem Env:VAR1` <br> `Set-Item -Path Env:VAR1 -Value "teste"`
| Persistir variáveis de ambiente | `/etc/enviromment` <br> `~/.bachrc` <br> `/etc/profile` | Windows + R,<br> type: `rundll32 sysdm.cpl,EditEnvironmentVariables` <br> or, type: `SETX FOO BAR` |
| Testar uma porta | `Telnet 192.168.1.55 80`<br> `nc -vz 192.168.1.55 80` | `Telnet 192.168.1.55 80` |
| Command substitution | `$(pwd)` or `` `pwd` `` | não tem |
| Flush DNS | `sudo killall -HUP mDNSResponder; say dns cleared` (mac) <br>`sudo /etc/init.d/networking restart` linux | `ipconfig /flushdns` |
| Watch file | `tail -f /var/log/syslog` | `Get-Content -Path "C:\scripts\test.txt" -Wait` |
| remove all | `rm -rf folder` | `Remove-Item -Force -Recurse folder` | 
| create file | `touch file.txt` | `echo > file.txt` |

## :white_check_mark: Git (exemplos)

### Stash


| Objetivo | Comando |
| -------- | ------- |
| Stash one file | `git stash push -m "message" -- test.txt` | 
| Stash untracked files | `git stash push -m "message" -u ` | 
| Apply staged too | `git stash apply --index` |
| Apply specific stashed | `git stash apply stash@{0}` |


## :white_check_mark: Docker (exemplos)

### Imagens

| Objetivo | Comando |
| -------- | ------- |
| Baixar uma imagem | `docker pull mcr.microsoft.com/dotnet/core/runtime:3.1` |
| Listar imagens: | `docker image list --all` |
| Remover uma imagem | `docker image rm mcr.microsoft.com/dotnet/core/runtime:3.1` |
| Remover imagens sem container associado | `docker image prune --all` |
| Criar/Executar container (1)  | `docker run --name dotnet31 -it --rm --privileged mcr.microsoft.com/dotnet/core/runtime:3.1 /bin/bash` |
| Criar/Executar container (2) | `docker run --name ubuntu -it --rm --privileged -p 445:445 ubuntu:20.04 /bin/bash` |
| Criar/Executar container (3) | `docker run -it --rm --entrypoint /bin/bash app1` (override entrypoint) |


### Containers

| Objetivo | Comando |
| -------- | ------- |
| Criar container | `docker container create -it --name dotnet31 --privileged -v c:\temp:/home mcr.microsoft.com/dotnet/core/runtime:3.1 /bin/bash` |
| Listar containers | `docker container list --all` |
| Iniciar container | `docker container start dotnet31` |
| Copiar arquivos para container | `docker cp bin/. dotnet31:home/bin` |
| Conectar em um container | `docker container exec -it dotnet31 /bin/bash` |
| Acompanhar logs | `docker logs --follow dotnet31` |
| Parar container | `docker container stop dotnet31` |
| Remover container | `docker container rm dotnet31` |
| Remover containers parados | `docker container prune` |
| Limpar tudo (!!!!) | `docker system prune --all` |

### Docker compose

| Objetivo | Comando |
| -------- | ------- |
| Docker compose "iterativo" | `sudo docker-compose run --rm service1` |

Exemplo de docker-compose.yml "iterativo":
```yml
version: "3"
services:
  service1:
    image: mcr.microsoft.com/dotnet/core/runtime:3.1
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

