# Données initiales à ajouter

Une fois le front et les micro-services qui run, nous pouvons ajouter quelques informations essentielles dans notre base
de données.

Dans un premier temps, connectez-vous à la base de données PostgreSQL locale.

<procedure title="Procédure de connexion" id="connect-to-db" type="steps" collapsible="true" default-state="collapsed">
    <tabs>
        <tab title="Depuis DataGrip">
            <ol>
                <li>Ajoutez une data source PostgreSQL</li>
                <li>
                    <p>Renseignez les informations ci-dessous comme suit</p>
                    <img src="datagrip_postgre_login.png"/>
                </li>
                <li>Connectez-vous</li>
            </ol>
        </tab>
        <tab title="Depuis WebStorm">
            <ol>
                <li>
                    <p>Installez le plugin <b>Database Tools and SQL for WebStorm</b></p>
                    <img src="database_plugin.png"/>
                </li>
                <li>Ajoutez une data source PostgreSQL</li>
                <li>
                    <p>Renseignez les informations ci-dessous comme suit</p>
                    <img src="datagrip_postgre_login.png"/>
                </li>
                <li>Connectez-vous</li>
            </ol>
        </tab>
    </tabs>
</procedure>

## Rôles

Dans la table `role`, ajoutez les valeurs suivantes.

<table style="none">
    <tr>
        <td>reader</td>
    </tr>
    <tr>
        <td>creator</td>
    </tr>
    <tr>
        <td>educational_manager</td>
    </tr>
    <tr>
        <td>admin</td>
    </tr>
</table>

Sauvegardez.

## Signalements

De la même manière, dans la table `report_reason`, définir les valeurs suivantes :

<table style="none">
    <tr>
        <td>Autre</td>
    </tr>
    <tr>
        <td>Plagiat</td>
    </tr>
    <tr>
        <td>Contenu inapproprié</td>
    </tr>
    <tr>
        <td>Spam</td>
    </tr>
    <tr>
        <td>Ressource incomplète</td>
    </tr>
</table>

## ScoLOMFR

> ScoLOMFR est le référentiel national de l'Éducation Nationale. C'est un gros dictionnaire que nous utilions
> pour indexer les ressources selon plusieurs niveaux (les classses des élèves) et les disciplines (les matières enseignées).
> Chaque année, une nouvelle version est mise à jour. Dans Quizéo, un panneau admin y est dédié.

Pour configurer ScoLOMFR, créez vous un compte sur votre Quizéo local et passez le en admin.

Rendez-vous dans le panneau administration puis "Scolom".

Demandez à Nicolas ou Hugo de vous passer la configuration et la version utilisée.

Copiez cette configuration dans le champs dédié puis cliquez sur "Mettre à jour".

Sinon, reprenez les informations ci-dessous :

**Version**
```json
8-0
```

**Configuration**
```json
[
    {
        "label": "Collège",
        "disciplineVocs": [
            "1273"
        ],
        "levelVocs": [
            "016"
        ]
    },
    {
        "label": "Lycée général et technologique",
        "disciplineVocs": [
            "1837",
            "6365",
            "6366",
            "7758",
            "6367",
            "6368",
            "6369",
            "7757",
            "1834"
        ],
        "levelVocs": [
            "123",
            "211",
            "088",
            "136",
            "142",
            "237"
        ]
    },
    {
        "label": "Voie professionelle",
        "disciplineVocs": [
            "099",
            "100",
            "794",
            "13685"
        ],
        "levelVocs": [
            "141",
            "165",
            "127",
            "027",
            "050",
            "213",
            "214",
            "215",
            "221",
            "222",
            "223",
            "227",
            "231"
        ]
    },
    {
        "label": "Enseignement supérieur",
        "disciplineVocs": [
            "6357",
            "7750"
        ],
        "levelVocs": [
            "162",
            "195",
            "198",
            "226",
            "065"
        ]
    },
    {
        "label": "Hors scolaire",
        "disciplineVocs": [],
        "levelVocs": []
    }
]
```