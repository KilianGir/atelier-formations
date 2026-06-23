# Atelier — Lecteur de formations

Lecteur de formations interactives **autonome et hors-ligne**, contenu dans **un seul fichier HTML**. Les cours sont stockés au format `.json` (données pures, aucun code exécuté depuis le fichier) et rendus avec termes annotés, schémas, frises, comparaisons, encadrés, sources citées et exercices auto-corrigés.

Pensé pour produire et distribuer rapidement des supports de formation — par exemple des modules pour apprenti·e·s — sans serveur, sans installation et sans dépendance externe.

---

## Pourquoi cet outil

- **Un seul fichier.** Aucun runtime, aucun build, aucune dépendance. On l'ouvre dans n'importe quel navigateur.
- **Hors-ligne et durable.** Bibliothèque et progression sont sauvegardées dans le `localStorage`. Rien ne quitte le poste.
- **Sûr par conception.** Le fichier de cours ne contient que des **données** : l'application n'exécute jamais de code provenant d'un `.json` importé.
- **Cours générables par IA.** Le format suit un gabarit documenté que l'on peut fournir à une IA pour produire une formation sur n'importe quel sujet.

---

## Deux usages

### Côté lecture (élève)
1. Ouvrir `index.html` dans un navigateur.
2. **Importer** une formation `.json` (bouton `＋` ou glisser-déposer), ou **charger la démo**.
3. Lire le cours : survol des termes colorés pour la définition, schémas interactifs, exercices corrigés.
4. La progression est mémorisée localement ; le tableau de bord `📊` la récapitule.
5. Mode **plein écran / immersif** (`⛶`) pour une lecture sans distraction.

### Côté création (formateur)
1. **Créer un cours vierge** ou ouvrir l'éditeur `✎` sur un cours existant.
2. Éditer le **JSON à gauche** → l'aperçu de droite se met à jour **en direct**. Clic sur un bloc de l'aperçu = saut vers la portion de JSON correspondante (et inversement).
3. Exporter :
   - **`⬇ JSON source`** — sauvegarde / versionnage du cours.
   - **`⬇ HTML élèves`** — génère un `.html` **autonome** (cours embarqué, éditeur masqué) à distribuer tel quel.

---

## Blocs et contenus disponibles

- **Texte enrichi** : `**gras**`, `*italique*`, termes annotés `[[clé]]` (info-bulle au survol), appels de source `{{n}}`.
- **Encadrés** : `note`, `tip` (astuce), `warn` (attention), `trap` (piège).
- **Graphiques** : barres, courbes, camembert.
- **Frise chronologique**, **tableau comparatif** (avantages / limites), **boîte de sources**.
- **Images** par URL web, avec crédit/licence obligatoire (avertissement visible si absent).
- **Exercices auto-corrigés** :
  - **QCM** (choix simple ou multiple),
  - **Texte à trous** (cloze),
  - **Question ouverte** corrigée par mots-clés.

---

## Format de fichier (aperçu)

```json
{
  "title": "Titre de la formation",
  "category": "Mécanique",
  "author": "optionnel",
  "color": "#2052bb",
  "description": "Résumé court pour la bibliothèque.",
  "lead": "Phrase d'accroche en italique.",
  "terms": [
    { "key": "infla", "label": "inflation", "color": "#b4540a",
      "summary": "Hausse générale et durable des prix." }
  ],
  "sections": [
    {
      "title": "Titre de la section",
      "blocks": [
        { "type": "paragraph", "text": "Texte avec un [[infla]] et un appel {{1}}." },
        { "type": "callout", "variant": "tip", "text": "Une astuce utile." }
      ],
      "sources": [
        { "author": "Nom", "text": "Titre", "year": "2020", "url": "https://..." }
      ]
    }
  ]
}
```

Seuls `title` et `sections` sont obligatoires. La documentation complète du format (tous les types de blocs et d'exercices) est **intégrée dans l'application** et accessible depuis l'éditeur — utile pour la fournir telle quelle à une IA.

---

## Installation

Aucune. Cloner ou télécharger le dépôt et ouvrir le fichier HTML dans un navigateur récent.

```bash
git clone https://github.com/KilianGir/atelier-formations.git
```

Pour une mise en ligne, n'importe quel hébergement statique (GitHub Pages, etc.) suffit.

---

## Confidentialité

Tout est local au navigateur : bibliothèque, progression et préférences vivent dans le `localStorage`. Les images référencées par URL sont chargées depuis le web ; le reste fonctionne entièrement hors-ligne.

---

## Licence

À définir (par ex. MIT).
