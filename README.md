# FluentPO

Outil quotidien d'apprentissage de l'anglais **pour Product Owner**. Objectif : B2 solide puis
C1, avec du vocabulaire produit réel, 25 minutes par jour. Page unique, autonome, sans build.
Ta progression est sauvegardée localement (localStorage) d'un jour à l'autre.

Base de contenu : **158 termes** et **44 phrases** extraits de l'ebook « L'anglais du Product
Owner » (Le Cercle des Langues), classés par thème (parties prenantes, produit, delivery,
roadmap, incident, feedback, rituels agiles, etc.).

## Fonctionnalités (tout est réel, rien de décoratif)

- **Suivi** : série de jours réelle, grille d'activité des 48 derniers jours, assiduité sur
  30 jours, temps passé dans le mois, programme du jour qui reflète ce que tu as vraiment fait.
- **Leçon** : lecture avec mots cliquables (ajout aux cartes), onglet **Audio** qui lit le texte
  en synthèse vocale (accent britannique, vitesse réglable), onglet **En contexte** avec phrases
  audio.
- **Grammaire** : quiz present perfect / past simple, score persistant, explications, une erreur
  crée une carte de rattrapage.
- **Vocabulaire** : les 158 termes navigables par thème + un « lot du jour » tournant.
  Prononciation audio (♪), « maîtrisé » et « à revoir » alimentent les cartes.
  **Ajout perso** : un formulaire (anglais + français) crée directement une carte mémo ;
  tes mots apparaissent dans le thème « ★ Mes ajouts », entrent dans la révision espacée,
  ont la prononciation (♪) pour t'entraîner à les dire, et sont exportés dans le CSV.
- **Cartes mémo** : vraie répétition espacée (boîtes de Leitner, intervalles 1, 2, 4, 9, 20
  jours), cartes dues du jour, prononciation, répartition par boîte.
- **Oral** : la phrase de référence est lue à voix haute, tu t'enregistres au micro, et sur
  Chrome la **reconnaissance vocale** transcrit ta phrase et calcule un score de prononciation
  (repli : enregistrement + réécoute sur les autres navigateurs).
- **Réglages** : interrupteurs persistants, heure de rappel modifiable, objectifs B2/C1
  éditables, **export CSV** de ta progression, réinitialisation.

## Lancer

```bash
python3 -m http.server 8777
```

Puis ouvrir http://localhost:8777/index.html (ou directement `index.html`).

## Compatibilité

- Synthèse vocale (prononciation, audio de leçon) : tous les navigateurs modernes.
- Reconnaissance vocale + score à l'oral : Chrome / Edge (autoriser le micro). Ailleurs, l'oral
  bascule sur enregistrement + réécoute pour t'auto-évaluer.
- Toute la progression vit dans le navigateur de l'appareil (localStorage). Pas de compte, pas
  de serveur.

## Structure

```
.
├── index.html            # app complète (UI + moteur + base vocabulaire intégrée)
└── assets/
    ├── portrait-1.jpg
    └── portrait-2.jpg
```

## Origine

Design conçu sur Claude Design (composant FluentPO), puis implémenté en application autonome et
enrichi avec le vocabulaire de l'ebook PO. Les photos de `assets/` sont des portraits
personnels, merci de ne pas les réutiliser.
