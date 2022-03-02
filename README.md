# Orquestração de contêineres com Docker

Qualquer dúvida, critica ou sugestão referente as aulas ou curso podem também serem sanadas no grupo do [telegram](https://t.me/joinchat/GzbydxdJZF0ZV-PCxcQdSQ).

Sintam-se a vontade em melhorar o conteúdo aqui criado!

<details>
  <summary>Principais comandos</summary>
  
## Instalar explorador de imagem
 https://github.com/wagoodman/dive

````bash
wget https://github.com/wagoodman/dive/releases/download/v0.9.2/dive_0.9.2_linux_amd64.deb
sudo apt install ./dive_0.9.2_linux_amd64.deb
````

#### Docker RUN
> Comando utilizado para criar um container

````bash
docker run --name newcontainer hello-world
docker run --name hello -d busybox sleep 3600
docker run --name site -d -p 80:80 nginx
````

#### Docker PS
> Lista os container em execução, para listar os que não estão precisamos colocar o parâmetro -a

````bash
docker ps -a
````
  
#### Docker INFO
> Exibe um sumuário dos nossos container, como também especificações do nosso docker

````bash
docker info
````

#### Docker EXEC
> Adiciona um processo a mais no container
> Vamos criar uma pasta dentro do container

````bash
docker exec hello mkdir teste
````

> Acessamos o container com o servico SH

````bash
docker exec -it hello sh
````

#### Docker STOP, START
> Paramos nosso container

````bash
docker stop hello
````
  
> Iniciamos nosso container

````bash
docker start hello
````

#### Docker LOGS
> coletamos o output do nosso container, ótimo para debugar uma aplicação

````bash
docker logs site
````

#### Docker PULL

````bash
docker pull hello-world
````

#### Docker COMMIT

````bash
docker commit --author="Luis Miguel" --message="Imagem com commit" hello hello
````

#### Docker TAG
> Preparando para docker hub

````bash
docker tag hello luistkd4/hello:1.0
````

> Trocando um nome de um repositório

````bash
docker tag hello-world ola-mundo
````

#### Docker LOGIN, LOGOUT
> Logar no repositório local, ou público. Por padrão logamos no Docker HUB

````bash
docker login <usuário>
````

#### Docker PUSH
> Vamos versionar nosso repositório/imagem ao docker hub

````bash
docker push luistkd4/hello:1.0
````

#### Docker SEARCH
> Procura por uma imagem no repositório

````bash
docker search <consulta>
````

#### Docker RM
> Remove um container previamente parado

````bash
docker rm newcontainer
````
> para remover um container em execução é nesessário o parâmetro -f

````bash
docker rm -f site
````

#### Docker RMI
> Remove um repositório/imagem local, se algum container estiver parado que utiliza essa imagem deverá passar o parâmetro -f

````bash
docker rmi hello-world
````
#### Docker EXPORT, IMPORT
> Exporta o container mergeando as suas camadas

````bash
docker export hello > export.tar
````

> Importa o arquivo gerado, criando uma imagem do container a partir dela

````bash
cat export.tar | docker import - hello-export:latest
````

#### Docker SAVE, LOAD
> Exporta a imagem em um arquivo

````bash
docker save luistkd4/hello:1.0 > save.tar
````

> Importa o arquivo gerado

````bash
docker load < save.tar
````

</details>
