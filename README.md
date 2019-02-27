# Instalação
    sudo apt-get update
    sudo apt-get install samba

# Backup e criação do smb.conf
    mv smb.conf smb.conf.bkp // backup
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
 
# Reiniciando o serviço samba para aplicar configurações
    service smbd restart
    service smbd status // Checa status do serviço (ON ou OFF)
    
# Criando usuários para valid users
## Caso tenha a necessidade de adicionar novos usuários(logins) ao servidor samba
    sudo useradd -m nomedousuario // criação do usuário
    
    smbpasswd -a nomedousuario // Insira a senha e confirma
    
# Sempre reinicie o serviço samba após cada modificação
    service smbd restart 
    
![](https://github.com/w1redl4in/.dotfiles/blob/master/Prints/2019-02-27--07:32:11:PM--1600900--scrot.png)
