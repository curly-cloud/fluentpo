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
- **Écrit** : deux onglets. **Traduction** FR↔EN (phrases de l'ebook) avec correction par
  comparaison mot à mot à une traduction de référence (diff surligné vert/rouge, mots manquants
  et en trop, score de proximité, audio). **Rédaction** : sujets PO concrets avec expressions
  cibles à réutiliser, checklist des expressions employées et corrigé modèle à comparer.
  Correction hors-ligne, sans IA ni compte (proximité à une réponse-modèle, pas une note absolue).
- **Réglages** : **synchronisation multi-appareils** (connexion par lien magique e-mail via
  Supabase ; ton vocabulaire perso et ta progression sont stockés dans ton compte et rechargés
  sur tous tes appareils, avec cache local hors-ligne), interrupteurs persistants, heure de
  rappel modifiable, objectifs B2/C1 éditables, **export CSV**, réinitialisation.

## Synchronisation (Supabase)

La synchro utilise Supabase (auth par lien magique e-mail + stockage dans les métadonnées du
compte, sans table à créer). Config nécessaire côté Supabase, une seule fois :
**Authentication → URL Configuration** → *Site URL* = `https://curly-cloud.github.io/fluentpo/`
et ajouter `https://curly-cloud.github.io/fluentpo/**` aux *Redirect URLs*. La clé `anon` est
publique par conception (sécurité assurée côté Supabase) ; ne jamais exposer la clé
`service_role`.

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
