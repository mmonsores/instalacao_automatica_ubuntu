# instalacao_automatica_ubuntu
Arquivo de exemplo para instalação automática do Ubuntu

Código montado seguindo informações no link abaixo:
https://canonical-subiquity.readthedocs-hosted.com/en/latest/reference/autoinstall-reference.html

Obs: Para criar uma senha (criptografada), é necessário acessar o Live CD, na instalação do Linux, abrir o terminal e  criar a contrassenha com o comando abaixo:
~$ mkpasswd seguido da sua senha

O terminal irá retornar com a senha criptografada em tamanho maior e cheia de caracteres.
Assim que criar, é necessário alimentar o arquivo autoinstall.yaml baixado, com a senha criada.
Depois é necessário adicionar o arquivo autoinstall.yaml na ISO Ubuntu.

Terminado os procedimentos, a instalação do Ubuntu nunca mais vai ser à mesma. Vai instalar com poucos cliques : )

Segue abaixo o código do arquivo autoinstall.yaml:


#cloud-config
autoinstall:
    version: 1
    identity:
        realname: 'SEU NOME'
        hostname: ubuntu-desktop
        username: SEU LOGIN
        password: 'CONTRASSENHA CRIADA'
    locale: pt_BR.utf8
    keyboard:
        layout: br
    timezone: "America/Sao_Paulo"   
    packages:
        - libreoffice
        - gimp
        - git
        - wget
    snaps:
        - name: spotify
          channel: stable
          classic: false
    codecs:
        install: true
    drivers:
        install: true
    updates: all
    shutdown: reboot
