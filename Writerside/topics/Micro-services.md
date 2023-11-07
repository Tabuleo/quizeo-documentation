# Micro-services

## Installer les dépendances

À la racine du projet, installer toutes les dépendances avec 

```Bash
yarn install
```

> **Bon à savoir**
>
> Yarn est setup en mode monorepo. Lorsque vous ajoutez des dépendances au projet, elles sont installées à la racine. Cependant, chaque micro-service a son package.json .
>
> Exemple: si vous voulez ajouter une dépendance depuis la racine, vous faites :
> 1. `cd <workspace>`
> 2. `yarn add <dep>`
> 3. `cd ..`
> 4. `yarn install`
> 
> Ou sinon (depuis la racine toujours) :
> 1. `yarn workspace <workspace> add <dep>`
> 2. `yarn install`
>
{style="note"}

## Lancer RabbitMQ

RabbitMQ est le serveur de messagerie qui va faire transiter les demandes entre l'API Gateway et les différents micro-services.

Depuis le fichier `docker-compose.yml`, exécuter le service : 

```yaml
rabbitmq:
    image: rabbitmq:3-management
    container_name: 'rabbitmq'
    environment:
      RABBITMQ_DEFAULT_USER: user
      RABBITMQ_DEFAULT_PASS: password
    restart: always
    ports:
      - "5672:5672"
      - "15672:15672"
    networks:
      - tabuleo-network
```

Vous pouvez tester que le service fonctionne bien en observant votre Docker Desktop et en allant sur [localhost:15672](http://localhost:15672).

Connectez-vous avec les identifiants renseignés dans le service.

## Lancer les BDD

> Les données de vos BDD sont enregistrées dans deux volumes situés dans le dossier database à la racine du micro-services.
> Ces données sont exclues de Git pour ne pas avoir de conflit avec les autres dév.

### PostgreSQL

Toujours dans le `docker-compose.yml`, exécuter le service :

```yaml
postgres:
    image: 'postgres'
    container_name: 'postgresdb'
    environment:
      POSTGRES_PASSWORD: nestjs
    ports:
      - "2345:5432"
    volumes:
      - ./database/postgres-volume:/var/lib/postgresql/superdata
    networks:
      - tabuleo-network
```

Les identifiants et mot de passe sont :
- _postgres_
- _nestjs_

### MongoDB

Maintenant, exécuter le service :

```yaml
mongo:
    image: mongo
    container_name: 'mongodb'
    networks:
      - tabuleo-network
    ports:
      - 27017:27017
    volumes:
      - ./database/mongo-volume:/data/db
    environment:
      MONGO_INITDB_ROOT_USERNAME: mongodb
      MONGO_INITDB_ROOT_PASSWORD: nestjsEnsuite, dans docker, aller dans le terminal du container.
```

## Récupérer les variables d'environnements

Rendez-vous sur [Vault](https://vault.quizeo.com).

Utilisez la méthode d'authentification GitHub et connectez-vous avec votre [PAT](https://docs.github.com/fr/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens).

Allez dans l’engine `quizeo-dev` puis dans chacun des micro-services. Copier-collez les valeurs dans un fichier `.env` 
situé dans chacun des micro-services correspondants.

## Lancer le projet

Il est recommandé de lancer tous les micro-services simultanément.

<tabs>
    <tab title="Depuis Webstorm">
        Sur Webstorm, vous avez les configurations pré-installés dans le dossier `.run`.
        Il suffit de lancer le <b>compound dev</b>, en haut à droite de l’écran.
        <img src="webstorm_config_ms.png" title="Webstorm run config" width="320"/>
    </tab>
    <tab title="En CLI">
        En étant à la racine du projet, exécutez la commande suivante :
        <code-block>
            yarn run start:dev
        </code-block>
    </tab>
</tabs>

