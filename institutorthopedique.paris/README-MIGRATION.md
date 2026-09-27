# Copie statique de www.institutorthopedique.paris

Aspiration réalisée le 27 septembre 2026 depuis le site public (WordPress 7.1 + Elementor Pro + thème PrimeCare + WP Rocket).

## Ce que contient ce dossier

- Les 62 URL du sitemap Yoast (accueil, 15 pages « Services », 16 fiches « Équipe médicale », contact, emploi, blog, catégories, tags, auteur), plus les pages de gabarits Elementskit (`_template-*.html`), soit 125 pages HTML.
- Tous les CSS, JS, polices, images (jpg/png/webp/avif/svg) et la vidéo d'accueil (77 Mo), soit 649 fichiers, 133 Mo.
- Les 69 « chunks » JavaScript chargés à la demande par Elementor (accordéons, compteurs, carrousels, lightbox…).
- Tous les liens internes ont été convertis en liens relatifs. Les suffixes `?ver=` ont été retirés des noms de fichiers.

Vérification : les 125 pages ont été ouvertes dans Chromium hors ligne, sans aucune requête vers l'ancien serveur et sans ressource manquante.

## Ce qui ne peut PAS être récupéré (côté serveur)

- Le back-office WordPress, la base de données, les fichiers PHP du thème et des plugins.
- Les comptes utilisateurs et les licences Elementor Pro / Elementskit.
- Il n'y a aucun formulaire de contact sur le site : la prise de rendez-vous passe par des liens Doctolib, donc rien ne dépend du serveur.

Liens externes conservés tels quels : Doctolib, Google Maps (iframe), LinkedIn.

## Pages de démonstration à supprimer avant mise en ligne

Le thème a laissé des articles de blog de démonstration en anglais sur des sujets dentaires
(`choosing-the-best-mouthwash…`, `the-benefits-of-dental-implants…`, `tag/dentalhealth`, etc.).
Ils sont indexés dans le sitemap actuel. Supprimer ces dossiers (et `blog/`, `category/`, `tag/`, `author/`) avant l'hébergement.

## Comment héberger

Déposer le contenu de ce dossier à la racine d'un hébergement web quelconque (OVH, o2switch, Hostinger, Netlify, Cloudflare Pages, GitHub Pages…). Chaque page est un `index.html` dans son dossier, donc les URL restent identiques (`/services/chirurgie-du-rachis/`).

Pour tester en local :

```
cd institutorthopedique.paris
python3 -m http.server 8000
```
puis ouvrir http://localhost:8000/

## Changement de DNS

1. Récupérer la main sur le nom de domaine (registrar : voir `whois institutorthopedique.paris`). Si le domaine est au nom du webmaster, demander un transfert ou un changement de titulaire.
2. Mettre en ligne la copie chez le nouvel hébergeur et vérifier avec un hôte de test.
3. Modifier l'enregistrement A (ou CNAME pour `www`) vers le nouvel hébergeur. Prévoir un certificat HTTPS (Let's Encrypt, automatique chez la plupart des hébergeurs).
4. Le site en ligne actuel restera visible jusqu'à la propagation (quelques heures au plus).
