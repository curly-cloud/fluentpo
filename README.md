# FluentPO

Application web d'apprentissage de l'anglais **orientée Product Owner**. Objectif : passer
d'un niveau B2 solide à un niveau C1 en s'appuyant sur du vocabulaire produit réel (agilité,
delivery, stakeholders), 25 minutes par jour.

Page unique, autonome, sans build ni dépendance : il suffit d'ouvrir `index.html`.

## Aperçu

Sept vues accessibles depuis la barre de navigation, toutes interactives :

| Vue | Contenu |
|-----|---------|
| **Suivi** | Tableau de bord : jalons B2/C1, série de régularité, programme du jour, révisions |
| **Leçon** | Lecture, audio et vidéo (onglets), expressions à envoyer en cartes mémo |
| **Grammaire** | Règle du jour + quiz avec feedback immédiat (present perfect vs past simple) |
| **Vocabulaire** | Termes PO en contexte, bascule « maîtrisé » qui met à jour la progression |
| **Cartes** | Cartes mémo recto/verso à retourner, répétition espacée |
| **Oral** | Répétition de phrases, enregistrement et comparaison de prononciation |
| **Réglages** | Rappel quotidien, objectifs B2/C1, préférences |

## Lancer

Les images sont chargées en chemins relatifs depuis `assets/`. Le plus simple :

```bash
python3 -m http.server 8777
```

Puis ouvrir http://localhost:8777/index.html

Ouvrir directement `index.html` en `file://` fonctionne aussi (JS et images inclus).

## Structure

```
.
├── index.html            # page unique + moteur de rendu JS
└── assets/
    ├── portrait-1.jpg
    └── portrait-2.jpg
```

## Sous le capot

Le design a été conçu sur [Claude Design](https://claude.ai/design) au format `.dc`
(template avec liaisons `{{ }}`, `onClick`, `style-hover`, `sc-if` / `sc-for`, et une logique
d'état `renderVals()`), normalement rendu par un runtime React.

Cette version est une **implémentation autonome** : un petit moteur de rendu en JavaScript pur
(≈150 lignes, sans framework) reproduit fidèlement les liaisons du format `.dc` et porte la
logique d'état d'origine. Aucune dépendance externe hormis les polices Google Fonts (DM Serif
Display, DM Sans, DM Mono).

### Paramètres configurables

En haut du `<script>` de `index.html`, objet `props` :

- `progressB2` (défaut `68`) — avancement vers le jalon B2 ; pilote l'étiquette et la barre.
- `reminderTime` (défaut `"12:00"`) — heure du rappel quotidien affichée dans Réglages.

## Licence

Projet personnel. Les photos de `assets/` sont des portraits personnels, merci de ne pas les
réutiliser.
