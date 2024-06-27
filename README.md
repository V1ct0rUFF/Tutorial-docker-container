# Tutorial-docker-container
Ensinar alguns comandos basicos docker
### Instalar Docker

curl -fsSL https://get.docker.com | bash

### Configuração dos Containers Docker

Criar um grupo docker: (caso não seja criado automaticamente)

```
sudo groupadd docker
```

Adicionar um usuario ao grupo: 

```
sudo usermod -aG docker $<nome do usuario>
```

Criar os volumes: (Leia o comentário abaixo)

```
docker volume create <nome do volume>
```
No passo de criação dos volumes é necessário que execute este comando para cada um dos volumes e os nomes de cada um deles sejam iguais aos das pastas disponiveis para download aqui. Por exemplo: 

```
docker volume create grafana
```

Copiar os volumes baixados para o destino: (Leia o comentário abaixo)

```
sudo cp -r * /var/lib/docker/volumes/
```

Para executar este comando é necessário que esteja no local onde os arquivos baixados estão.

Criar rede docker:

```
docker network create <nome da rede>
```

Subir os containers:

```
docker run -d --user root --network <nome da rede> --mount type=volume,src=grafana,dst=/var/lib/grafana --name=container_grafana -p 3000:3000 grafana/grafana-oss (o container do grafana)
```

Comandos Básicos Docker:

Docker container ls = Lista os containers que estão em execução
Docker container ls -a = Lista até os container parados
Docker container stop = Pausa o container
Docker container start = Reinicia o container
Docker container rm ID_do_Container = Deleta o container em excução.


