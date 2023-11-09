# Dump des BDD

Faire un dump des BDD peut-être pratique pour alimenter l'environnement de test ou en local.

## PostgreSQL

*Comment faire un dump d’une base PostgreSQL et l’appliquer sur un autre serveur avec Datagrip et `pg_dump`.*

<procedure type="steps" title="Procédure">
    <step>
        <b>Installer les outils nécessaire</b>
        <p><i>Sur Mac avec Brew</i></p>
        <code-block>
            brew install libpq
        </code-block>
    </step>
    <step>
        <b>Mettre à jour le PATH</b>
        <ul>
            <li>
                <p>Pour Mac M1 :</p>
                <code-block>
                    echo 'export PATH="/opt/homebrew/opt/libpq/bin:$PATH"' >> ~/.zshrc
                    source ~/.zshrc
                </code-block>
            </li>
            <li>
                <p>Pour Mac Intel :</p>
                <code-block>
                    echo 'export PATH="/usr/local/opt/libpq/bin:$PATH"' >> ~/.zshrc
                    source ~/.zshrc
                </code-block>
            </li>
        </ul>
    </step>
    <step>
        <b>Dump depuis Datagrip</b>
        <p>Clique-droit sur la base de données dans l'explorer > <code>Import/Export</code> > <code>Export with 'pg_dump'</code></p>
        <p>Renseignez les informations suivantes :</p>
        <ul>
            <li><code>Path to pg_dump</code> : exécutez <code>which pg_dump</code> dans votre terminal, puis copiez-coller le path dans ce champs</li>
            <li><code>Statements</code>: Copy</li>
            <li>Cochez <code>Clean database</code></li>
            <li>Spécifiez le chemin de sortie du fichier</li>
            <li><b>Run</b></li>
        </ul>
    </step>
    <step>
        <b>Restore depuis Datagrip</b>
        <p>Cique-droit sur la base de données dans l'explorer > <code>Import/Export</code> > <code>Restore with 'psql'</code></p>
        <p>Renseignez les informations suivantes :</p>
        <ul>
            <li><code>Path to psql</code> : exécutez <code>which psql</code> dans votre terminal, puis copiez-coller le path dans ce champs</li>
            <li>Spécifiez le chemin du fichier dump précédemment</li>
            <li>Run</li>
        </ul>
    </step>
    <step>
        <b>La base de données devrait être complétement restaurée.</b>
    </step>
</procedure>

## MongoDB

*Comment faire un dump d’une base MongoDB et l’appliquer sur un autre serveur en CLI.*

<procedure type="steps" title="Procédure">
    <step>
        <b>Installer les outils</b>
        <p><i>Sur Mac avec Brew</i></p>
        <code-block>
            brew tap mongodb/brew
            brew install mongodb/brew/mongodb-database-tools
        </code-block>
    </step>
    <step>
        <b>Dump</b>
        <p>
            Renseignez bien le user et le password selon les identifiants, ainsi que <code>authSource</code> qui permet de renseigner la base de données que l'on veut dump.
        </p>
        <code-block>
            mongodump --uri "mongodb://user:password@localhost:27017/?authSource=dbname" --out nomDuFichierDeBackup
        </code-block>
    </step>
    <step>
        <b>Restore</b>
        <p>
            Si dans le repertoire backup, il y a un dossier avec le nom de la bdd à renommer, il n’est pas nécessaire de préciser la <code>dbName</code> dans l’URI.
        </p>
        <code-block>
            mongorestore --uri "mongodb://user:password@localhost:27017/dbName" pathDuDossierDeBackup
        </code-block>
    </step>
    <step>
        <b>La base de données devrait être complétement restaurée.</b>
    </step>
</procedure>