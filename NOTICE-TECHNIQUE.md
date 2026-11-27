# Site 22h13.fr — notice technique de reprise

Collectif 22h13min (association loi 1901, Cournonterral, Hérault)
Notice rédigée le 27/11/2026. Version du site sauvegardée : commit `618dd67` du 27/11/2026.

Cette notice s'adresse à toute personne qui reprendrait la gestion du site (informaticien, webmaster, bénévole). Jusqu'ici, le site a été construit et mis à jour par Claude (assistant IA d'Anthropic), à la demande de Samuel Zaroukian.

## 1. En bref

- **Adresse** : https://22h13.fr (HTTPS actif). Aussi joignable à https://clicetretiens.github.io/22h13, qui redirige.
- **Technique** : site statique, uniquement du HTML, du CSS et un peu de JavaScript écrits à la main. Pas de CMS, pas de base de données, pas d'étape de compilation, pas de dépendance à installer.
- **Hébergement** : GitHub Pages, gratuit, depuis le dépôt GitHub `clicetretiens/22h13`, branche `main`, à la racine.
- **Nom de domaine** : 22h13.fr, chez OVH.
- **Statut** : phase de test, le site n'est **pas indexé** par les moteurs de recherche (voir §5).

Pour modifier le site, il suffit de modifier un fichier HTML et de le pousser sur la branche `main` : GitHub Pages republie en 1 minute environ.

## 2. Les comptes (à demander à Samuel ou Amélie Zaroukian)

Ce fichier est public (le dépôt l'est) : aucun identifiant ni mot de passe n'y figure. Une version plus complète est sauvegardée par le collectif. Les accès se demandent aux responsables du collectif.

| Service | Compte | Rôle |
|---|---|---|
| GitHub | `clicetretiens` | Code et hébergement du site |
| OVH | compte de Samuel Zaroukian (identifiant à lui demander) | Nom de domaine 22h13.fr et zone DNS |
| Gmail | 22h13min@gmail.com | Mail officiel du collectif, affiché sur le site |

Le compte GitHub `clicetretiens` héberge aussi d'autres projets de Samuel (`clic-et-retiens`, `lutrin`) : ne pas y toucher.

## 3. Organisation des fichiers

```
/
├── index.html          Accueil
├── collectif.html      Le collectif : texte, cartes d'Amélie et Samuel, artistes associés, Les Murmures de Lou
├── projets.html        Les « portes » des 4 spectacles
├── agenda.html         Les dates
├── contact.html        Mail, adresse, SIRET
├── artistes.html       Ancienne page, redirige vers collectif.html#equipe (à garder pour les vieux liens)
├── img/                Images communes (logo, portes, photos)
├── soleil-noir/        Mini-site du spectacle Soleil noir (index.html + images)
├── milo/               En chemin, Milo
├── retrace/            [Re]trace
├── cotonn/             Cotonn
├── samuel/             Page de Samuel Zaroukian
├── amelie/             Page d'Amélie Zaroukian
├── robots.txt          Disallow: / (phase de test)
├── CNAME               22h13.fr (nécessaire à GitHub Pages pour le domaine)
└── .nojekyll           Empêche GitHub Pages de traiter le site avec Jekyll
```

Chaque page est autonome : son CSS et son JavaScript sont écrits dans le fichier lui-même. Les liens entre pages sont relatifs.

**Adresses imprimées** : des QR codes sur des cartes de visite et des invitations papier pointent vers https://22h13.fr, https://22h13.fr/samuel/, https://22h13.fr/soleil-noir/, https://22h13.fr/milo/, https://22h13.fr/retrace/ et https://22h13.fr/cotonn/. **Ne jamais renommer ni déplacer ces dossiers**, sinon les supports imprimés mèneront à une page d'erreur.

## 4. Services extérieurs utilisés

- **Google Fonts** (polices : Oswald, Open Sans, Cormorant Garamond, Barlow, Lora, Nunito, Fredoka, Amatic SC, Luckiest Guy, Archivo Black, Public Sans…). Chaque page charge les siennes.
- **SoundCloud** : lecteurs intégrés (compte https://soundcloud.com/samuel-zaroukian) sur les pages Samuel, Cotonn et Soleil noir.
- **YouTube** (via youtube-nocookie.com) : teasers réalisés par Corinne Gomez (Gom's).
- Liens simples vers Instagram et Midi Libre.

Rien d'autre : pas de statistiques, pas de cookies, pas de formulaire.

## 5. Ouverture aux moteurs de recherche

Le site est volontairement caché à Google tant que les textes ne sont pas tous relus. Quand les responsables le demanderont :

1. remplacer le contenu de `robots.txt` par `User-agent: *` / `Allow: /` ;
2. retirer de **chaque** page HTML la ligne `<meta name="robots" content="noindex, nofollow">`.

## 6. Nom de domaine et DNS (OVH)

- **22h13.fr** acheté le 25/11/2026, domaine seul (sans hébergement OVH), **expire le 25/11/2027**, renouvellement annuel.
- Zone DNS réglée le 25/11/2026 :
  - 4 enregistrements A sur `@` : 185.199.108.153, 185.199.109.153, 185.199.110.153, 185.199.111.153 (adresses de GitHub Pages) ;
  - CNAME `www` → `clicetretiens.github.io.` ;
  - conservés : NS, SPF, MX (mx1/mx2/mx3.mail.ovh.net), CNAME `ftp`, TXT `@` « 1|www.22h13.fr ».
- GitHub, Settings > Pages : domaine personnalisé `22h13.fr`, « Enforce HTTPS » coché.
- **Échéance à surveiller** : une messagerie OVH (Zimbra) liée au domaine se renouvelle automatiquement le **05/10/2027**. Vérifier avant cette date si elle devient payante et la supprimer dans ce cas.

## 7. Modifier et publier

1. Cloner : `git clone https://github.com/clicetretiens/22h13.git`
2. Modifier les fichiers (un éditeur de texte suffit). Pour tester, ouvrir les pages dans un navigateur, ou lancer `python -m http.server` à la racine et aller sur http://localhost:8000.
3. `git commit` puis `git push` sur `main`. En ligne en 1 minute environ.

Les messages de commit sont en français et décrivent la modification (« Page Samuel : … », « Cotonn : … »). L'historique complet : `git log`.

## 8. Repères de style

- Couleurs du collectif : framboise `#C0295E`, bleu nuit `#061F5F`, crème `#FFF3DC`.
- Menu principal : Accueil, Le collectif, Projets, Agenda, Contact.
- Chaque projet a sa propre identité visuelle (couleurs de son affiche), un menu centré avec une entrée « Accueil » (accueil du projet) et, en haut à gauche, un lien framboise « ← Les projets ».
- Pages de Samuel et d'Amélie : lien « ← Le collectif ».
- Page Projets : les portes restent étroites et verticales (230 px de large maximum, 460 px de haut, 52 px d'écart ; 2 rangées de 2 sur téléphone). C'est un code visuel auquel le collectif tient.
- Soleil noir est un « site dans le site » : il doit fonctionner seul (un QR code y mène directement).
- Textes justifiés.

## 9. Règles de contenu

- Ne rien inventer : crédits, lieux, dates et prix viennent uniquement des responsables du collectif.
- Garder le ton propre à chaque spectacle.
- Les choix éditoriaux détaillés (ce qu'il faut écrire, ce qu'il ne faut pas remettre) sont dans le document de suivi tenu avec Claude, dont le collectif garde une copie.

## 10. Restaurer le site depuis cette sauvegarde

Si le dépôt GitHub était perdu :

- **Avec l'historique** : `git clone historique-git-2026-11-27.bundle 22h13` recrée le dépôt complet, avec tous les commits. Puis créer un nouveau dépôt GitHub, `git remote set-url origin <nouvelle adresse>`, `git push -u origin main`, activer GitHub Pages (branche `main`, racine) et y remettre le domaine `22h13.fr`. Si le compte GitHub change, adapter le CNAME `www` dans la zone DNS OVH.
- **Sans git** : `code-du-site-2026-11-27.zip` contient les fichiers du site, prêts à déposer chez n'importe quel hébergeur de fichiers statiques.

Cette sauvegarde est un instantané au 27/11/2026. Le dépôt GitHub reste la version de référence : en cas de doute, c'est lui qui fait foi.
