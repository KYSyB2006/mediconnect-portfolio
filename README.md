# MediConnect — Portfolio Data & Analytics

Étude de cas présentant mon travail sur **MediConnect**, une plateforme de recherche et de prise
de rendez-vous médicaux développée en équipe de 4 dans le cadre des UE **WE4A / SI40 / WE4B**.

**Belva Samyra Yonta Kenne** — yontabelva@gmail.com

---

## Mon périmètre

Sur les quatre domaines répartis dans l'équipe, j'ai porté les deux suivants :

| Rôle | Domaine | Livrables |
|---|---|---|
| **P2** | Recherche & Filtres | API de géolocalisation (Haversine, API BAN), collection `search_logs`, dashboard Power BI Géographie |
| **P3** | RDV & Disponibilités | Calcul des créneaux disponibles, gestion des rendez-vous, dashboard Power BI Activité |

La page est structurée selon la méthode **CAR** (Contexte · Action · Résultat), avec deux cas
d'étude détaillés et les extraits de code réels correspondants.

---

## Compétences illustrées

- **SQL** — modélisation relationnelle, migrations versionnées, requêtes d'agrégation (jointures, `GROUP BY`, `CASE WHEN`)
- **Qualité de données** — détection et correction de doublons avec réattribution des clés étrangères
- **NoSQL** — MongoDB pour les logs de recherche et d'activité
- **Géospatial** — formule de Haversine, géocodage via l'API Base Adresse Nationale
- **BI** — Power BI, Power Query M, pipeline d'export CSV automatisé
- **Restitution** — dashboard analytics intégré (Angular + Chart.js)

---

## Structure du dépôt

```
.
├── index.html      Page du portfolio (autonome : CSS et JS inclus)
├── images/         Captures des dashboards
├── .nojekyll       Désactive le traitement Jekyll de GitHub Pages
└── README.md
```

La page est **entièrement autonome** : aucune dépendance à installer, aucune étape de build.
Seules les polices sont chargées depuis Google Fonts, avec repli sur les polices système.

---

## Publier sur GitHub Pages

1. Créer un dépôt **public** (par exemple `mediconnect-portfolio`).
2. Y déposer le contenu de ce dossier, puis pousser sur `main`.
3. Dans le dépôt : **Settings → Pages**.
4. Sous *Build and deployment*, choisir **Deploy from a branch**, brancher `main` et le dossier `/ (root)`.
5. Enregistrer. Le site est en ligne après une à deux minutes à l'adresse
   `https://<pseudo>.github.io/mediconnect-portfolio/`.
6. **Une fois l'URL connue**, ouvrir `index.html` et remplacer les trois occurrences de
   `PSEUDO` (balises `og:url`, `og:image`, `twitter:image`) par ton identifiant GitHub.
   Sans cette étape, le lien partagé sur LinkedIn s'affichera sans vignette.

> GitHub Pages sur un dépôt privé nécessite un abonnement payant — d'où le dépôt public dédié,
> distinct du code source de MediConnect qui reste privé.

---

## Captures d'écran

Les deux pages du rapport **MediConnect_Geographie.pbix** sont déjà intégrées dans `images/` :

| Fichier | Contenu |
|---|---|
| `powerbi-recherches.png` | Page *Activité & recherches* — densité par ville, top villes, évolution mensuelle, couverture des spécialités |
| `powerbi-geographie.png` | Page *Géographie & accès aux soins* — densité par département, spécialités non trouvées par rayon, recherches vs RDV |
| `apercu.png` | Vignette de partage (1200 × 630) générée à partir de la première page |

Pour en ajouter d'autres (dashboard Activité, Stock, admin Angular), déposer le PNG dans `images/`
puis dupliquer un bloc `<figure class="shot" data-shot>` dans `index.html`. Toute figure dont le
fichier est absent se masque automatiquement, il n'y a donc jamais d'image cassée affichée.

---

## Chiffres clés du rapport

- **200** recherches journalisées sur 6 mois, dont **83 %** géolocalisées
- **20,2 km** de rayon de recherche moyen
- **49** praticiens référencés sur 7 villes, dont 16 à Paris
- Constat principal : les deux spécialités les plus recherchées (dentiste et neurologue, 24 recherches
  chacune) comptent respectivement **0** et **2** praticiens, tandis que la médecine générale représente
  35 % de l'offre pour la 8ᵉ place en demande

---

## Note sur les données

Les chiffres proviennent du jeu de données du projet pédagogique : 200 recherches sur 6 mois et
49 praticiens. C'est suffisant pour valider le pipeline, les algorithmes et faire ressortir des
tendances nettes, mais pas pour en tirer des conclusions statistiques à l'échelle nationale.
