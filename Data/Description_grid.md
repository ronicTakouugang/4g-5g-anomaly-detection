# Description des données géographiques (Milan Grid)

## Présentation

Les données du **Telecom Italia Big Data Challenge** proviennent de plusieurs entreprises et de différentes sources de données (télécommunications, météo, actualités, réseaux sociaux et électricité). Chaque source possède ses propres standards de représentation géographique.

Afin de faciliter l'analyse et la comparaison entre les différentes zones de la ville, les organisateurs ont choisi de découper la ville de Milan en une grille régulière composée de **10 000 cellules carrées**.

Cette grille sert de référence spatiale pour l'ensemble des données du projet.

Le fichier contenant ces informations géographiques est disponible à l'adresse suivante :

https://doi.org/10.7910/DVN/QJWLFU

---

## Informations générales

- **Type de fichier :** GeoJSON (`.geojson`)
- **Taille :** environ 3 Mo
- **Nom du fichier :**

```text
milano-grid.geojson
```

---

## Description de la grille

La ville de Milan est divisée en :

```text
10 000 cellules carrées (grids)
```

Chaque cellule possède une taille approximative de :

```text
235 mètres × 235 mètres
```

Chaque carré représente donc une petite zone géographique de la ville dans laquelle les activités télécom (SMS, appels, Internet) sont agrégées.

Cette subdivision permet de réaliser des analyses spatiales précises, par exemple :

- identifier les zones de forte activité réseau ;
- détecter des anomalies localisées ;
- comparer le comportement de différents quartiers ;
- analyser les déplacements et les concentrations de population.

---

## Système de coordonnées

Les coordonnées géographiques sont exprimées dans le système de référence :

```text
WGS 84 (EPSG:4326)
```

Il s'agit du système de coordonnées géographiques le plus utilisé dans le monde, notamment par :

- Google Maps ;
- OpenStreetMap ;
- les GPS ;
- les outils SIG (Systèmes d'Information Géographique).

Les coordonnées sont exprimées en :

- latitude ;
- longitude.

---

# Description des variables

Le fichier `milano-grid.geojson` contient principalement les informations suivantes :

| Colonne | Description |
|----------|-------------|
| square id | Identifiant unique d'une cellule de la grille de Milan. |
| geometry | Géométrie de la cellule exprimée au format GeoJSON et projetée dans le système WGS84 (EPSG:4326). |

---

## Exemple de structure

```json
{
  "square_id": 4456,
  "geometry": {
    "type": "Polygon",
    "coordinates": [
      [
        [9.1501,45.4623],
        [9.1522,45.4623],
        [9.1522,45.4644],
        [9.1501,45.4644],
        [9.1501,45.4623]
      ]
    ]
  }
}
```

Dans cet exemple :

- `square_id = 4456` correspond à une cellule particulière de la grille de Milan ;
- `geometry` contient les coordonnées des sommets du carré.

---

# Utilité dans le projet

Le fichier `milano-grid.geojson` est essentiel pour ajouter une **dimension spatiale** aux données de télécommunications.

Il permet notamment de :

- représenter les données sur une carte ;
- construire des cartes de chaleur (Heatmaps) ;
- identifier les zones de congestion réseau ;
- visualiser les anomalies détectées ;
- réaliser des analyses spatio-temporelles ;
- étudier l'évolution du trafic selon les quartiers de la ville.

Dans le cadre de ce projet de **détection d'anomalies dans le trafic des réseaux cellulaires**, ce fichier permettra de localiser précisément les anomalies détectées et d'analyser leur répartition géographique dans la ville de Milan.