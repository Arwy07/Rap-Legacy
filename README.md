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

## Télécharger sans Git

Sur GitHub, choisir **Code → Download ZIP**, extraire l'archive et ouvrir un terminal dans le dossier contenant `go.mod`, `main.go` et `assets/`. Le dépôt étant privé, le compte GitHub doit y avoir accès.

Installer [Go](https://go.dev/dl/), rouvrir le terminal et vérifier `go version`. Le projet déclare Go 1.25.0 et Ebitengine 2.8.8 : conserver les versions du dépôt pour le premier essai. Les documentations actuelles du moteur peuvent concerner une version plus récente.

## Compiler et lancer sous Windows

Depuis la racine du projet, dans PowerShell :

```powershell
go mod download
go run .
```

Pour compiler puis lancer un exécutable local :

```powershell
New-Item -ItemType Directory -Force bin
go build -o bin/rap-legacy.exe .
.\bin\rap-legacy.exe
```

Conserver le terminal dans la racine : le programme charge les images et la musique par des chemins relatifs. Copier uniquement l'exécutable ailleurs ne suffit pas pour lancer le jeu.

Sous Linux/macOS : créer le dossier bin avec `mkdir -p bin`, compiler avec `go build -o bin/rap-legacy .`, puis exécuter `./bin/rap-legacy`. Un environnement graphique et les dépendances système adaptées à Ebitengine 2.8.8 peuvent être nécessaires.

## Première partie et commandes

1. Attendre la fin de l'introduction ou appuyer sur Entrée.
2. Depuis le menu, ouvrir l'écran des sauvegardes et choisir une nouvelle partie.
3. Saisir le nom, choisir une classe avec 1, 2 ou 3, puis valider avec Entrée.
4. Se déplacer ; près du marchand ou de la zone de combat, utiliser E pour interagir.
5. Ouvrir l'inventaire avec Tab, choisir un objet avec les flèches puis l'utiliser avec Entrée.

| Contexte | Touches relevées dans le code |
|---|---|
| Menus et choix en combat | Haut/bas et Entrée ; clic gauche sur les boutons des menus concernés |
| Déplacement | W, A, S, D ; adapter son confort à la disposition du clavier |
| Interaction marchand / combat | E dans la zone correspondante |
| Inventaire | Tab ouvrir/fermer, haut/bas sélectionner, Entrée utiliser |
| Forgeron / craft | F ouvrir, haut/bas et Entrée, Échap revenir |
| Création de partie | Saisie du nom, Retour arrière, 1 Lyricistes / 2 Performeurs / 3 Hitmakers et Entrée |
| Suppression d'une partie | Dans l'écran des sauvegardes, Suppr sélectionne la suppression ; une seconde pression confirme |

## Sauvegarder, arrêter et restaurer une partie

Fermer la fenêtre pour arrêter. Les données sont enregistrées dans `saves/saves.json`, créé par le programme et exclu de Git. Le modèle contient le nom, la classe, l'inventaire, la position et certaines statistiques : il ne faut pas supposer qu'il mémorise tous les états temporaires.

Avant une mise à jour ou une réparation, fermer le jeu puis copier le dossier saves dans un emplacement privé. Pour restaurer une partie, remettre cette copie dans la racine de la même version du projet avant de relancer. Ne pas publier ses sauvegardes personnelles.

## Dépannage

| Problème | Vérification |
|---|---|
| go introuvable | Installer Go puis rouvrir le terminal |
| go.mod introuvable | Se placer dans le dossier contenant go.mod |
| Modules non téléchargés | Vérifier la connexion et relancer go mod download |
| Images ou musique absentes | Lancer depuis la racine, garder assets et menu/menu.mp3 à leur place |
| Fenêtre impossible à ouvrir | Utiliser une session de bureau et un pilote graphique fonctionnel |
| Sauvegarde inaccessible | Vérifier les droits d'écriture ; garder une copie avant réparation |
| Pas de son | Vérifier le périphérique audio, son volume et le fichier menu/menu.mp3 |

## Modifier le projet

Changer une fonctionnalité à la fois dans les fichiers concernés, compiler avec `go build ./...`, puis tester le comportement dans le jeu. Conserver les chemins des ressources. Ne pas supprimer go.sum ni mettre à jour toutes les dépendances pour résoudre un simple problème de dossier.

## Organisation

| Chemin | Contenu |
|---|---|
| `main.go`, `icon.go` | Démarrage et icône de fenêtre |
| `game/` | Combat, personnage, inventaire, carte, sauvegardes et interface |
| `menu/` | Menu et piste audio |
| `assets/` | Images, animations et police |

## Contributions et provenance

Projet réalisé en binôme : contribution d'Arwy07 aux sauvegardes, à l'inventaire, au marchand et au craft ; contribution du second développeur aux visuels, menus, combats et à la musique. Les potions et l'intégration générale ont été réalisées ensemble, selon le README du projet d'origine.

Le chemin de la musique du menu a été corrigé pour fonctionner depuis la racine. Aucune licence supplémentaire n'est attribuée aux ressources : leur provenance et leurs droits doivent être confirmés avant redistribution publique.

## À propos

Prototype pédagogique réalisé en binôme en une semaine. Les sources et ressources nécessaires sont incluses ; les sauvegardes restent locales. Le chemin de la musique est prévu pour un lancement depuis la racine du projet.
