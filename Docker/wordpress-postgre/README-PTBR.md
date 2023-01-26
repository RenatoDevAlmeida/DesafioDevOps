# Desafio DevOps

Criação de um Dockerfile de Ubuntu/Wordpress/Postrgre + certificado ssl instalado. 

## 🚀 Começando

### 📋 Pré-requisitos
Basicamente para rodar o projeto é necessário o Docker instalado no seu S.O um terminal.

### 🔧 Instalação
 
1 - criar a image com o comando (sem aspas)
    "docker build -t nome-da-imagem-image -f local-do-arquivo/Dockerfile ."

    A flag "-t" significa "tag" e isso dá o nome a imagem.
    A flag "-f" especifica o arquivo Dockerfile para gerar a imagem.
    A flag " ." significa que a imagem será construída na pasta atual.

2 - Criar o Container com o comando (sem aspas)
    "docker-compose up"

    Esse comando cria o container do projeto, mas existe um outro que 
    além de criar o Container, ele roda o mesmo em background, ou seja, 
    o usuário poderá manipular, sem a necessidade de para-lo.

## ⚙️ Dockerfile e docker-compose








```

