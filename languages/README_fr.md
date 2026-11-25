# VKT LinkClean - Nettoyeur de liens

[English](../README.md) | [中文](README_zh.md) | [Español](README_es.md) | [Deutsch](README_de.md) | [日本語](README_ja.md) | Français

Avant de partager, retirer le poids du traçage. Collez une URL et VKT LinkClean nomme chaque paramètre supprimé, démonte les redirections et les pages AMP, puis rend un lien propre. Tout se passe sur votre appareil : aucun lien ne quitte le navigateur.

## Points forts

- **Un collage, un lien propre** — collez une URL ou reprenez l'onglet en cours.
- **Rien ne disparaît en silence** — chaque paramètre retiré est nommé, avec la valeur que le site aurait reçue.
- **Copie en URL ou en Markdown** — le Markdown est construit à partir du vrai titre : `[titre](url)`.
- **Mode par lot** — accepte une liste d'URL, mais aussi un paragraphe, un e-mail ou une conversation. Seuls les liens sont réécrits, le texte autour reste intact.
- **Les paramètres fonctionnels restent** — seuls 61 noms de traçage connus et 12 familles de préfixes (`utm_`, `ga_`, `mtm_`, `piwik_`, `_hs` et d'autres) sont retirés.
- **Pro : démonter les redirections** — Google, YouTube, Facebook, Reddit, DuckDuckGo, LinkedIn, Zhihu, Douban, Jianshu, SSPAI, VK, Slack, Outlook Safe Links, Skimlinks, Tumblr, Medium, Pocket, plus Bing, Weibo, Proofpoint et la forme générique `/redirect?url=` — en local, récursif, trois sauts au maximum.
- **Pro : résolution AMP** — `cdn.ampproject.org/c/s/`, `google.com/amp/s/` et un `/amp` final reviennent à la page canonique.
- **Pro : règles par site** — `amazon.com` garde `th` et `psc` pendant que le reste est supprimé. Le domaine le plus précis l'emporte et les sous-domaines en héritent. Un clic sur un paramètre retiré le conserve définitivement sur ce site.
- **Pro : historique et compteurs** — recherche par lien, titre ou domaine, copie du lien d'origine, export JSON ; plus des compteurs de liens nettoyés et de paramètres retirés.

## Gratuit vs Pro

| | Gratuit | Pro |
|---|---|---|
| Nettoyage d'un lien (liste intégrée complète) | ✅ | ✅ |
| Copie Markdown / presse-papiers / interrupteur de fragments | ✅ | ✅ |
| Copie automatique après nettoyage | ✅ | ✅ |
| Taille du lot | 10 liens | illimitée |
| Export TXT | ✅ | ✅ |
| Export CSV / JSON | — | ✅ |
| Paragraphes contenant plusieurs liens | jusqu'à 10 | ✅ |
| Démonter redirections et AMP | simple indication | ✅ |
| Règles par site + conservation en un clic | — | ✅ |
| Historique | 10 entrées | 100, avec recherche et lien d'origine |
| Paquets de règles (import/export) | — | ✅ |
| Détail des sites les plus fréquents | — | ✅ |

Une clé active deux navigateurs ; la retirer libère cette place. Vérification environ toutes les deux heures, la licence en cache fonctionne hors ligne ; un échec ne verrouille rien.

## Utilisation

1. Cliquez sur l'icône VKT LinkClean. Si la page en cours porte des paramètres de traçage, le champ est déjà rempli.
2. Appuyez sur « Nettoyer le lien ». Le résultat affiche l'URL propre, chaque paramètre retiré sous forme d'étiquette et, avec une licence et en cas de redirection, la chaîne résolue.
3. Copiez le lien, copiez-le en Markdown, ouvrez-le ou envoyez-le au mode par lot.
4. Un paramètre ne devait pas partir ? Cliquez dessus dans le résultat : il rejoint la liste des conservés de ce site.

## Confidentialité

- Les liens ne quittent jamais le navigateur. Chaque règle est une opération locale sur des chaînes ; **aucune redirection n'est téléchargée pour connaître sa destination**.
- Ni analyse d'audience, ni télémétrie, ni identifiant publicitaire, ni pixel de suivi.
- L'historique, les réglages et les compteurs vivent dans `chrome.storage.local` et peuvent être effacés à tout moment.
- La seule requête réseau est la vérification de licence : clé, identifiant d'installation aléatoire, id du plugin et métadonnées de navigateur basiques.
- Le presse-papiers n'est lu qu'en appuyant sur Coller, et écrit qu'en copiant ou lorsque la copie automatique est active.

## Autorisations

| Autorisation | Usage |
|---|---|
| `storage` | Enregistrer réglages, règles personnalisées, historique et état de licence en local |
| `activeTab` | Lire l'URL de la page courante, seulement après un clic sur l'icône |
| `clipboardWrite` | Écrire le lien propre lors d'une copie ou de la copie automatique |
| `clipboardRead` | Lire le presse-papiers uniquement en appuyant sur Coller, jamais en arrière-plan |
| `https://api.annmax1983.com/*` | Activation et vérification de licence uniquement ; jamais un lien |

Pas de content script, pas d'accès `<all_urls>`, pas d'autorisation `tabs`, pas d'autorisation `downloads` : VKT LinkClean ne peut voir le texte d'aucune page.

## Navigateurs pris en charge

Chrome et Edge (Manifest V3, Chrome 116+). Une version Firefox est prévue.

## Développement

```bash
npm install        # seule dépendance de développement : terser
npm run locales    # génère les six _locales depuis tools/make-locales.js
npm run icons      # génère les icônes
npm test           # node --test : nettoyage, redirections, règles par site, i18n, câblage du panneau
npm run build      # minifie et empaquette → publish/linkclean-v{version}.zip
node tools/shoot.js  # captures 1280×800 et promo rendues dans Chrome réel
```

> Ce dépôt sert uniquement à présenter le projet ; le code source complet n’est pas publié. Installez VKT LinkClean depuis les stores officiels.

## Liens

- Site web : https://annmax1983.com
- Page de l'extension : https://annmax1983.com/extensions/linkclean
- Licence et prix : https://annmax1983.com/checkout?plugin=linkclean
