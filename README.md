# LSCSO Website - Webserver Package v2.0

## 📁 Fichiers inclus

```
webserver/
├── index.html           → Page principale (Tailwind CSS + Responsive)
├── script.js            → Logique JavaScript (animations, interactivité)
├── styles.css           → Animations personnalisées
├── config.json          → Configuration du site
├── logo.png             → Logo agent (image par défaut)
├── *.webp              → Photos agents individuelles (Bilel.webp, Buck.webp, Tom.webp, etc.)
└── README.md            → Ce fichier
```

## 🚀 Déploiement sur votre Webserver

1. **Copier tous les fichiers** dans le répertoire racine de votre webserver
2. **Vérifier les images** : `logo.png`, `Bilel.webp`, `Buck.webp`, `Tom.webp`, etc.
3. **Accéder au site** via `http://votre-domaine.com/` ou `http://localhost/`
4. **Aucune dépendance** - Tout est CDN ou inline

## 📦 Dépendances (CDN)

Le site utilise uniquement des CDN publics (pas d'installation requise) :
- **Tailwind CSS v3** : `https://cdn.tailwindcss.com`
- **Font Awesome 6.4.0** : `https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css`

## ✨ Fonctionnalités v2.0

✅ Design moderne avec **Tailwind CSS**  
✅ **15 agents** avec profils détaillés et hiérarchie complète  
✅ Photos individuelles haute qualité (format `.webp`)  
✅ Grille responsive (1 col mobile, 2 col tablet, 3 col desktop)  
✅ Cartes agent enrichies avec :
   - Photo de profil (h-72)
   - Grade et matricule personnalisé
   - Division et spécialité
   - Statut en service
   - Coordonnées (email, téléphone, bureau/secteur)
   - Évaluation stars (★★★★☆)
✅ Formulaire de contact fonctionnel  
✅ Animations fluides au défilement  
✅ Système de couleurs coordonné par grade  
✅ Support multilingue (Français)

## 👥 Structure Organisationnelle

### Hiérarchie (15 agents)

```
1. James Sawyer       → Sheriff              (LSC-001) ★★★★★
2. Maria Santos       → Under Sheriff        (LSC-002) ★★★★☆
3. Robert Harper      → Commander            (LSC-003) ★★★★★
4. Jennifer Hernandez → Captain              (LSC-004) ★★★★☆
5. Michael Chen       → Deputy Sergeant II   (LSC-005) ★★★★☆
6. Jessica Williams   → Deputy Sergeant I    (LSC-006) ★★★★☆
7. David Thompson     → Deputy Sergeant I    (LSC-007) ★★★★☆
8. Amanda Johnson     → Deputy Sheriff II    (LSC-008) ★★★★☆
9. Carlos Garcia      → Deputy Sheriff II    (LSC-009) ★★★★☆
10. Thomas Patterson  → Deputy Sheriff II    (LSC-010) ★★★★☆
11. Sarah Mitchell    → Deputy Sheriff I     (LSC-011) ★★★★☆
12. Kevin Anderson    → Deputy Sheriff I     (LSC-012) ★★★★☆
13. Tom Scolla        → Deputy Sheriff I     (LSC-013) ★★★★☆
14. Bilel Rio         → Deputy Sheriff I     (LSC-014) ★★★★☆
15. Buck Karen        → Deputy Sheriff I     (LSC-015) ★★★★☆
```

### Divisions
- Direction Générale (1 agent)
- Opérations (1 agent)
- Enquêtes Criminelles (1 agent)
- Sécurité Communautaire (1 agent)
- Patrouille (3 agents)
- Centre d'Appels (1 agent)
- Patrouille générale (6 agents)
- Administration (1 agent)

## 🎨 Système de Couleurs

Chaque agent a sa propre couleur coordonnée :

```
Amber-300/400/500     → Sheriff / Direction
Blue-300/400/500      → Under Sheriff / Opérations
Pink-300/400/500      → Commander / Enquêtes
Purple-300/400/500    → Captain / Sécurité
Indigo-300/400/500    → Deputy Sergeant II
Green-300/400/500     → Deputy Sergeant I #1
Teal-300/400/500      → Deputy Sergeant I #2
Orange-300/400/500    → Deputy Sheriff II #1
Red-300/400/500       → Deputy Sheriff II #2
Rose-300/400/500      → Deputy Sheriff II #3
Pink-300/400/500      → Deputy Sheriff I #1
Lime-300/400/500      → Deputy Sheriff I #2
Fuchsia-300/400/500   → Deputy Sheriff I #3
Cyan-300/400/500      → Deputy Sheriff I #4
Violet-300/400/500    → Deputy Sheriff I #5
```

## 📝 Sections du Site

1. **Navigation** - Menu fixe avec logo et liens
2. **Hero** - Section d'accueil avec animation
3. **À Propos** - Mission, valeurs et statistiques
4. **Services** - 6 cartes de services
5. **Équipe** - Grille des 15 agents (5 rangées × 3 colonnes)
6. **Contact** - Formulaire + informations
7. **Footer** - Liens et copyright

## 📝 Structure Carte Agent

```html
<div class="group bg-slate-800 border-t-4">
  <!-- Section photo (h-72) -->
  <div class="relative h-72 bg-gradient-to-br">
    <img src="[agent-image].webp" alt="[nom]">
  </div>
  
  <!-- Contenu -->
  <div class="p-7">
    <!-- En-tête : grade, nom, matricule -->
    <div class="text-center mb-5">
      <h3 class="text-3xl font-black">{{NOM}}</h3>
      <p class="text-sm font-semibold">{{MATRICULE}} • {{TITRE}}</p>
      <div class="flex justify-center gap-1">★★★★☆</div>
    </div>
    
    <!-- Informations détaillées -->
    <div class="space-y-3">
      <!-- Grade -->
      <!-- Division -->
      <!-- Spécialité -->
      <!-- Statut -->
    </div>
    
    <!-- Coordonnées -->
    <div class="bg-gradient-to-r p-4 rounded-lg">
      <p>Email, Téléphone, Bureau/Secteur</p>
    </div>
    
    <!-- Bouton -->
    <button>Dossier Complet</button>
  </div>
  
  <!-- Décoration coin -->
  <div class="absolute top-0 right-0 w-20 h-20"></div>
</div>
```

## 🔧 Configurations Serveur

### Apache (.htaccess)
```apache
<IfModule mod_rewrite.c>
    RewriteEngine On
    RewriteCond %{REQUEST_FILENAME} !-f
    RewriteCond %{REQUEST_FILENAME} !-d
    RewriteRule ^ index.html [QSA,L]
</IfModule>
```

### Nginx
```nginx
location / {
    try_files $uri $uri/ /index.html;
}
```

### Node.js (Express)
```javascript
app.use(express.static('webserver'));
app.get('*', (req, res) => res.sendFile(__dirname + '/index.html'));
```

## 📊 Statistiques du Projet v2.0

- **Tailwind CSS v3** : Framework utilitaire complet
- **Font Awesome 6.4.0** : 1600+ icônes
- **Agents** : 15 profils avec hiérarchie
- **Responsive** : Mobile-first (md, lg breakpoints)
- **Images** : Format `.webp` optimisé
- **Performance** : ~150KB HTML + images optimisées
- **Browsers** : Chrome, Firefox, Safari, Edge (moderne)

## ⚡ Performance & Optimisations

✅ **Grille CSS responsive** : Ajustement automatique cols  
✅ **CDN global** : Tailwind et Font Awesome  
✅ **Images webp** : Format moderne compressé  
✅ **Pas de framework lourd** : Vanilla JavaScript uniquement  
✅ **Lazy loading** recommandé pour images  
✅ **Minification** en production fortement recommandée  

## 🔐 Sécurité

✅ **XSS Protection** : Aucun innerHTML dynamique dangereux  
✅ **CORS** : Pas d'appels externes sensibles  
✅ **HTTPS** : Fortement recommandé en production  
✅ **Validation** : Formulaire côté client et serveur  

## 🎯 Modification des Agents

Pour modifier ou ajouter des agents, éditez directement dans `index.html` :

1. Localisez le commentaire `<!-- Agent XX -->`
2. Modifiez les valeurs `LSC-XXX`, `grade`, `division`, etc.
3. Changez les couleurs Tailwind : `border-[color]-400`, `from-[color]-600`, etc.
4. Remplacez `Bilel.webp` par votre image `.webp`

## 📞 Support

Pour ajouter des fonctionnalités :
- **Backend formulaire** : Intégrez PHP, Node.js, Python
- **Base données** : Connectez un CMS ou API
- **Authentification** : Ajoutez OAuth/JWT si besoin

## 📜 Licence

© 2025 Los Santos County Sheriff's Department - Tous droits réservés

---

**Version 2.0** - Mise à jour complète avec 15 agents, photos individuelles et hiérarchie organisationnelle.

**Prêt pour la production !** 🚀
