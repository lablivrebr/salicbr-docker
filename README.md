# SalicBR com Docker
Repositório com arquivos para "dockerizar" o sistema SALIC: códigos para criar "images" e "containers" do sistema SALIC utilizando-se do Docker

## Comandos para utilização do docker neste projeto 

> **Nota**
> - Instale o Git, Docker e o Docker Compose na sua máquina para utilizar este projeto https://www.docker.com/

### Como usar
Este projeto deve ser utilizado para a montagem e execução do sistema SALIC em um ambiente configurado com os serviços oferecidos pelo Docker. 

Para usar este projeto e montar o sistema SALIC em sua máquina execute apenas 4 passos principais

> - **Baixe o projeto**
```cmd
git clone https://github.com/lablivrebr/salicbr-docker.git
```
> - **Monte as imagens**
```
docker-compose build
```

>> Serão criadas as duas "images" docker do projeto: 
>> - uma para o serviço de Banco de Dados (que pode ser acessada a partir do Dockerfile mantido no diretório "postgresql_9.3") 
>> - outra para o serviço web (Dockerfile da raiz do projeto)

> - **Execute os containers**
```
docker-compose up -d
```

> - **Acesse a aplicação**
```
http://localhost/
```

A imagem a seguir ilustra como este projeto deve ser utilizado:
![Como utilizar este projeto](/arquivos/DockerFluxoUtilizacao.jpg)

### Como foi projetado
Projetamos o Docker mantendo em mente o conceito de micro serviços. Neste sentido, dividimos o ambiente de instalação do sistema SALIC em dois serviços:

- Um serviço para o Banco de Dados da aplicação
  - utilizando duas imagens: 
    - debian:jessie
    - postgres:9.3 - postgresql 9.3
- Um outro serviço para o Servidor de Aplicação
  - utilizando basicamente:
    - java:openjdk-7-jdk (debian:jessie)
    - Java7 (OpenJdk)
    - Maven3
    - Git - command line
    - Jboss7.1.1 
    - postgresql-client
    - vim
    - GOG - deploy

A imagem a seguir ilustra a utilização do Docker foi projetada para o sistema GOG; isto ajuda a entender como utilizar o docker para montar os serviços envolvidos:
![Como foi projetada a utilização do Docker no sistema GOG](/arquivos/DockerMontagemAmbiente.jpg)
