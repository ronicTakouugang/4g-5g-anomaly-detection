# Description des données

## Présentation du dataset

Ce jeu de données provient du **Telecom Italia Big Data Challenge**. Il regroupe plusieurs types de données (télécommunications, météo, réseaux sociaux, actualités et consommation électrique) collectées dans la ville de Milan et la province du Trentin en Italie.

Dans le cadre de ce projet, nous utilisons uniquement les **données de télécommunications de la ville de Milan**, disponibles à l'adresse suivante :

https://doi.org/10.7910/DVN/EGZHFV

Le dataset est distribué sous licence **Open Database License (ODbL)** et est hébergé par Harvard Dataverse.

---

## Période de collecte

Les données couvrent la période allant du :

- **01 novembre 2013**
- au **01 janvier 2014**

Le dataset contient **62 fichiers**, soit un fichier par jour.

Exemples de fichiers :

```text
sms-call-internet-mi-2013-11-01.txt
sms-call-internet-mi-2013-11-02.txt
...
sms-call-internet-mi-2014-01-01.txt
```

Chaque fichier :

- a une taille comprise entre **200 et 300 Mo** ;
- contient environ **4 millions de lignes**.

L'ensemble du dataset représente donc plus de **240 millions d'observations**, ce qui en fait un véritable jeu de données de type **Big Data**.

---

## Organisation spatiale

La ville de Milan est découpée en plusieurs milliers de petites zones carrées appelées **grids**.

Chaque grille possède un identifiant unique appelé :

```text
Grid ID
```

Chaque observation est donc associée :

1. à une zone géographique ;
2. à un instant précis ;
3. à une activité télécom observée durant les 10 minutes suivantes.

---

## Résolution temporelle

Les données sont agrégées par intervalles de :

```text
10 minutes
```

Le champ `Time Interval` correspond au début de l'intervalle en millisecondes depuis le 1er janvier 1970 (Unix Timestamp).

L'heure de fin peut être obtenue en ajoutant :

```text
600 000 millisecondes
```

soit :

```text
10 minutes
```

Par exemple :

```text
1383260400000
```

correspond au :

```text
01/11/2013 00:00:00
```

et représente l'activité entre :

```text
00:00 et 00:10
```

---

# Description des variables

Le fichier ne contient pas d'en-tête. Il est composé de **8 colonnes**.

| Colonne | Description |
|----------|-------------|
| Grid ID | Identifiant de la zone géographique de Milan. |
| Time Interval | Début de l'intervalle d'observation en millisecondes. |
| SMS-in activity | Volume de SMS reçus durant l'intervalle. |
| SMS-out activity | Volume de SMS envoyés durant l'intervalle. |
| Call-in activity | Volume d'appels reçus durant l'intervalle. |
| Call-out activity | Volume d'appels émis durant l'intervalle. |
| Internet traffic activity | Nombre de CDR (Call Detail Records) générés par le trafic Internet mobile. |
| Country code | Indicatif téléphonique international du pays d'origine ou de destination des communications. |

---

## Signification d'une observation

Chaque ligne du dataset représente :

> Le volume d'activités télécom (SMS, appels et Internet) observé dans une zone donnée de Milan pendant une période de 10 minutes.

Exemple :

| Grid ID | Date | SMS In | SMS Out | Call In | Call Out | Internet | Country |
|----------|------|---------|----------|----------|-----------|-----------|----------|
| 4456 | 01/11/2013 08:00 | 10 | 12 | 5 | 7 | 350 | 39 |

Cette observation signifie que :

- dans la zone **4456** ;
- entre **08h00 et 08h10** ;
- 10 SMS ont été reçus ;
- 12 SMS ont été envoyés ;
- 5 appels ont été reçus ;
- 7 appels ont été émis ;
- 350 enregistrements de trafic Internet ont été générés.

---
