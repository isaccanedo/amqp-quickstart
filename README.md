Início rápido do Quarkus AMQP 1.0
============================

Este projeto ilustra como você pode interagir com o AMQP 1.0 (Apache Artemis neste início rápido) usando MicroProfile Reactive Messaging.
As instruções completas estão disponíveis em https://quarkus.io/guides/amqp.

## Inicie o aplicativo no modo de desenvolvimento

Em um primeiro terminal, execute:

```bash
> mvn -f amqp-quickstart-producer quarkus:dev
```

Em um segundo terminal, execute:

```bash
> mvn -f amqp-quickstart-processor quarkus:dev
```  

Em seguida, abra seu navegador em `http://localhost:8080/quotes.html`, e clique no botão "Solicitar Orçamento".

## Crie o aplicativo no modo JVM

Para criar os aplicativos, execute:

```bash
> mvn -f amqp-quickstart-producer package
> mvn -f amqp-quickstart-processor package
```

Como estamos executando no modo _prod_, precisamos fornecer um broker AMQP 1.0.
The [docker-compose.yml](docker-compose.yml) file starts the broker and your application.

Inicie o broker e os aplicativos usando:

```bash
> docker compose up --build
```

Em seguida, abra seu navegador em `http://localhost:8080/quotes.html`, e clique no botão "Solicitar Orçamento".
 

## Crie o aplicativo no modo nativo

Para criar os aplicativos em executáveis nativos, execute:

```bash
> mvn -f amqp-quickstart-producer package -Pnative  -Dquarkus.native.container-build=true
> mvn -f amqp-quickstart-processor package -Pnative -Dquarkus.native.container-build=true
```

O `-Dquarkus.native.container-build=true` instrui o Quarkus a construir executáveis nativos Linux 64bits, que podem rodar dentro de containers.  

Em seguida, inicie o sistema usando:

```bash
> export QUARKUS_MODE=native
> docker compose up
```
Then, open your browser to `http://localhost:8080/quotes.html`, and click on the "Request Quote" button.
