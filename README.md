# Rap-Legacy

Jeu de rôle en 2D dans l'univers du rap, développé en Go avec Ebitengine dans le cadre d'un projet étudiant réalisé en binôme en une semaine.

## Fonctionnalités

- Combats au tour par tour : punchlines, égo et statistiques du personnage.
- Choix de classe, progression et gestion des ressources.
- Inventaire, consommables, marchand et système de craft.
- Sauvegardes locales au format JSON.
- Menus, animations et ambiance sonore.

## Lancer le projet

Prérequis : Go 1.25 ou compatible, environnement graphique et sortie audio. Les ressources sont chargées depuis le dossier courant : lancer les commandes à la racine du dépôt.

```sh
git clone https://github.com/Arwy07/Rap-Legacy.git
cd Rap-Legacy
go mod download
go run .
```

Pour compiler : `go build -o bin/rap-legacy .` (ajouter `.exe` sous Windows). Exécuter ensuite depuis la racine pour retrouver `assets/` et `menu/`. Les sauvegardes sont créées automatiquement dans `saves/` et ne sont pas versionnées.

## Organisation

| Chemin | Contenu |
|---|---|
| `main.go`, `icon.go` | Démarrage et icône de fenêtre |
| `game/` | Combat, personnage, inventaire, carte, sauvegardes et interface |
| `menu/` | Menu et piste audio |
| `assets/` | Images, animations et police |

## Contributions et provenance

Projet réalisé en binôme : contribution d'Arwy07 aux sauvegardes, à l'inventaire, au marchand et au craft ; contribution du second développeur aux visuels, menus, combats et à la musique. Les potions et l'intégration générale ont été réalisées ensemble, selon le README du projet d'origine.

Sources récupérées depuis le dossier local du projet ; ancien historique Git, exécutable et sauvegardes personnelles exclus. Le chemin de la musique du menu a été corrigé pour fonctionner depuis la racine. Aucune licence supplémentaire n'est attribuée aux ressources : leur provenance et leurs droits doivent être confirmés avant redistribution publique.

## État et limites

Prototype pédagogique conservé pour présenter le travail réalisé. La compilation et les vérifications effectuées sont consignées dans [VALIDATION.md](VALIDATION.md). Une compilation réussie ne remplace pas une vérification des interactions en jeu.
