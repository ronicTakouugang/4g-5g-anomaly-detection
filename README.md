# Détection d'anomalies réseau 4G/5G — Milan

Analyse du trafic télécom de la ville de Milan (Telecom Italia Big Data Challenge)
pour détecter des anomalies de trafic Internet mobile, avec une approche inspirée
du framework académique **DiNATrAX** (Maudoux & Boumerdassi, IEEE ICC 2024).

## Données

- Source : [Telecom Italia Big Data Challenge](https://doi.org/10.7910/DVN/EGZHFV) (Harvard Dataverse, licence ODbL)
- Période : 1er novembre 2013 → 1er janvier 2014 (62 fichiers, un par jour)
- Détail complet des champs et du format : [`Data/Description_data.md`](Data/Description_data.md)

## Méthodologie

Le pipeline (dans [`eda.ipynb`](eda.ipynb)) encode, pour chaque grille et chaque jour,
le profil horaire de trafic Internet en une séquence de lettres (quantiles),
puis compare cette séquence à un profil de référence (même grille, même jour de
la semaine) via la distance de Damerau-Levenshtein. Un score z est ensuite calculé
sur ces distances pour repérer les jours anormaux, qui sont enfin recoupés avec un
calendrier d'événements (jours fériés, matchs à San Siro...).

## Visualisation 3D

Un tableau de bord interactif ([`viz/milan_3d.html`](viz/milan_3d.html)) permet
d'explorer le trafic heure par heure, jour par jour, avec les anomalies détectées
mises en évidence sur une carte 3D de Milan (deck.gl + MapLibre GL JS).

Pour le lancer localement (nécessite un serveur HTTP à cause de CORS) :

```bash
cd viz
python -m http.server 8000
# puis ouvrir http://localhost:8000/milan_3d.html
```
