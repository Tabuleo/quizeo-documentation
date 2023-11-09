# Sauvegarde des instances

Notre infrastructure fonctionne sur trois noeuds. Nous avions la possibilité de sauvegarder juste les PVC ou bien
l'ensemble de l'instance.

Par simplicité, nous avons décidé de **sauvegarder les instances** dans leur entièreté. Cela comprend les PVC, les 
deployments, les SVC etc...

## Fonctionnement des sauvegardes

Les sauvegardes suivent une **rotation de 7 jours** automatisées par OVH. C'est-à-dire une **sauvegarde quotidienne 7 jours d'affilés**.

Au delà du 7ème jour, la sauvegarde est supprimée.

### Tarification

Chaque sauvegarde est facturée **0,01 € HT/mois/Go**.

Sachant que le poids d'une instance est d'environ **40Go**, qu'il y a **3 instances** sauvegardées sur **7 jours**.
Nous pouvons faire simplement le calcul suivant :

```tex
TotalHT=0.01 * ~40 * 3 * 7 ~= 8,40e HT / mois
```


## Restaurer une instance

_todo..._