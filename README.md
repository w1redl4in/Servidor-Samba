# Instalação
    sudo apt-get update
    sudo apt-get install samba

# Entrando no diretório de configuração
    cd /etc/samba
    sudo su // Virando root

# Backup e criação do smb.conf
    cp smb.conf smb.conf.bkp // backup
    nano smb.conf

# Configuração do smb.conf
    [global] // Configuração global
      workgroup = xxxx // Nome de domínio
      security = user // Login e senha necessário para logar
      
      
    [Nome da sua Pasta]
      comment = xxxx // Algum comentário (Aparece sobre mouse-hover)
      path = /home/lain/Documents/Samba-fatec // Exemplo do caminho da minha pasta compartilhada
      valid users = xxxx // Login do usuário para efetuar o login
      writeable = yes // Pode ser editado
      browseable = yes // Pode ser acessado de outros dispositivos
      
 # Criando usuários para valid users
## Caso tenha a necessidade de adicionar novos usuários(logins) ao servidor samba
    sudo useradd -m nomedousuario // criação do usuário
    smbpasswd -a nomedousuario // Insira a senha e confirma
    
# Ajustando permissões para outros usuários
    chmod o+x /nomedapasta/    
 
# Reiniciando o serviço samba para aplicar configurações
    service smbd restart
    service smbd status // Checa status do serviço (ON ou OFF)
### Sempre reinicie o serviço samba após cada modificação
  
# Acessando o samba 
## Windows
    Abra o executar(Win+R) e entre com: \\seuip e entre com login/senha ~ Exemplo: \\192.168.2.1
    
## Linux
    Abra qualquer File Manager e entre com: smb://seuip ~ Exemplo: smb://192.168.15.1
    
## Android
    Baixe o app SWAT ou Gerenciador de arquivos + na Playstore e acesse via ip
   
# Meu samba com minhas config
   
![](https://github.com/w1redl4in/.dotfiles/blob/master/Prints/2019-02-27--07:32:11:PM--1600900--scrot.png)
