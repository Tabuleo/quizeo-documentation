# Front-end

## Installation des dépendances

À la racine du projet, installer toutes les dépendances avec

```bash
yarn install
```

## Récupérer les variables d’environnements

Rendez-vous sur [Vault](https://vault.quizeo.com).

Utilisez la méthode d'authentification GitHub et connectez-vous avec votre [PAT](https://docs.github.com/fr/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens).

Allez dans l’engine `quizeo-dev` puis `quizeo-front`, copier-coller les valeurs dans un fichier `.env.local` à la racine
du projet.

## Lancer le projet

<tabs>
    <tab title="Depuis Webstorm">
        Sur Webstorm, vous avez les configurations pré-installés. Il vous suffit de lancer le script `dev`.
        <img src="webstorm_config_front.png" title="Configuration Webstorm" width="320"/>
    </tab>
    <tab title="En CLI">
        Executez la commande ci-dessous.
        <code-block>
        yarn run dev
        </code-block>
    </tab>
</tabs>



