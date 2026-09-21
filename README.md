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
- **Leçon du jour** : **12 leçons qui tournent chaque jour** (une par thème PO). Chaque leçon
  réunit une lecture (mots cliquables → cartes), l'onglet **Audio** (synthèse vocale, vitesse
  réglable), l'onglet **En contexte**, et surtout **tout le vocabulaire du thème du jour** à
  apprendre (écouter ♪ / ajouter en carte). La Leçon, le lot de vocabulaire et la Grammaire sont
  alignés sur le même thème et changent chaque jour.
- **Grammaire du jour** : un point de grammaire par leçon (present perfect, for/since, modaux,
  conditionnels, passif, discours rapporté, comparatifs…) avec règle, exemples et quiz scoré ;
  une erreur crée une carte de rattrapage.
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

La synchro utilise Supabase : authentification **e-mail + mot de passe** (aucun e-mail envoyé)
et stockage des données dans les métadonnées du compte (`user_metadata`), sans table SQL à
créer. Config nécessaire côté Supabase, une seule fois :
**Authentication → Providers → Email** → désactiver **« Confirm email »** (pour que la création
de compte connecte directement, sans e-mail de confirmation). La clé `anon` est publique par
conception (sécurité assurée côté Supabase) ; ne jamais exposer la clé `service_role`.

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
