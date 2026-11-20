# Mon Budget

Application web de budget personnel, simple et autonome : saisissez vous-même vos revenus et dépenses, puis suivez-les sur l’année et au-delà. Aucune connexion bancaire, aucun compte à créer.

**[Essayer en ligne](https://khaldiahmed91-cyber.github.io/Mon-Budget/)**

---

## Fonctionnalités

- **Tableau de bord** annuel : revenus, dépenses (hors épargne), solde, taux d’épargne, graphiques et tableau mois par mois
- **Transactions** : ajout, modification, suppression, filtres et recherche
- **Récurrences** mensuelles ou annuelles, avec date de fin optionnelle et action « Arrêter… »
- **Catégories et sous-catégories** : création, renommage, suppression ; détail dépliable avec montants et pourcentages
- **Budgets** mensuels par catégorie, avec suivi de l’avancement
- **Suivi d’épargne pluriannuel** : encours cumulé d’une année sur l’autre, versements, retraits, objectif
- **Calculatrice** de projection sur N années (1, 5, 10, 20, 30 ou saisie libre), avec évolution annuelle composée optionnelle
- **Export / import** JSON et export CSV
- **Import de relevé bancaire** (CSV, Excel .xlsx, OFX/QFX, QIF), entièrement local, avec détection des virements internes, liste **Mes comptes** et livrets d’épargne
- **Assistant IA optionnel** (Qwen en ligne ou Ollama en local), désactivé par défaut
- **Mode sombre** et affichage adapté au mobile


## Importer un relevé bancaire

Vous pouvez intégrer les opérations de n’importe quelle banque, sans créer de connecteur spécifique. Tout se passe **dans votre navigateur** : le fichier n’est jamais envoyé à un serveur.

1. Dans votre espace client bancaire, exportez un relevé (souvent *Relevés*, *Historique* ou *Téléchargements*) au format **CSV**, **Excel (.xlsx)**, **OFX/QFX** ou **QIF**.
2. Dans Mon Budget, ouvrez **Transactions** ou **Paramètres** et cliquez sur **Importer un relevé bancaire**.
3. Vérifiez le mapping détecté (date, libellé, montant ou colonnes Débit/Crédit), corrigez-le si besoin, puis validez l’aperçu. Les colonnes sont mémorisées pour le prochain fichier du même type.
4. Les libellés courants (magasins, transporteurs, abonnements, salaire, etc.) sont classés automatiquement ; vous pouvez corriger une catégorie, et ce choix est réutilisé ensuite.
5. Les lignes déjà présentes (même date, même montant, libellé proche) sont proposées décochées, avec le badge **Déjà importé**. Vous pouvez **Annuler le dernier import**.

**Formats pris en charge**

- CSV / TXT (séparateur `;`, `,`, tabulation ou `|` ; UTF-8 ou Windows-1252 / ISO-8859-1, fréquents en France)
- Excel **.xlsx** (analyseur intégré, sans bibliothèque externe). Les anciens fichiers **.xls** doivent être réenregistrés en .xlsx ou CSV.
- OFX / QFX et QIF

Les montants au format français (`1 234,56`, `12,50-`, etc.) et les dates `jj/mm/aaaa`, `aaaa-mm-jj`, etc. sont reconnus, y compris les dates « série » d’Excel. Les opérations importées sont des transactions ponctuelles : elles alimentent le budget mensuel et annuel, le cash disponible et les budgets par catégorie.

Dans **Paramètres > Virements internes / Épargne**, vous pouvez lister **Mes comptes** (noms de vos banques, par ex. Revolut, N26, Crédit Agricole) : les virements et recharges vers ces comptes sont exclus des totaux. Les livrets (Livret A, LDDS, LEP, PEL, CEL) sont reconnus comme épargne. Les mouvements de bourse, crypto ou poches d’investissement sont exclus par défaut ; une option permet de les compter comme épargne si vous le souhaitez.

## Assistant IA (optionnel)

Désactivé par défaut. Rien ne quitte l’appareil tant que vous n’activez pas un fournisseur dans **Paramètres**.

### Qwen en ligne (DashScope)

1. Créez une clé API sur le [Model Studio / DashScope](https://www.alibabacloud.com/help/en/model-studio/get-api-key) (région internationale par défaut).
2. Dans Paramètres, choisissez **Qwen en ligne (DashScope)**, collez la clé, et éventuellement l’URL (défaut : `https://dashscope-intl.aliyuncs.com/compatible-mode/v1`) et le modèle (`qwen-plus`, `qwen-turbo` ou `qwen-max`).
3. La clé reste dans ce navigateur (`localStorage` dédié). Elle n’est **jamais** incluse dans une sauvegarde JSON, sauf case explicitement cochée (déconseillé). Aucune clé n’est présente dans le dépôt public.

### Qwen local (Ollama)

1. Installez [Ollama](https://ollama.com) puis `ollama pull qwen2.5` (ou `qwen3`).
2. Lancez le serveur, par exemple :

```bash
OLLAMA_ORIGINS=https://khaldiahmed91-cyber.github.io,http://localhost,capacitor://localhost \
OLLAMA_HOST=0.0.0.0:11434 ollama serve
```

`OLLAMA_ORIGINS=*` est plus simple en local. Pour un iPhone sur le même Wi-Fi, indiquez l’IP du Mac dans l’app (ex. `http://192.168.1.20:11434`).

3. Le site GitHub Pages est en HTTPS : Safari bloque souvent `http://localhost` (contenu mixte). Chrome autorise localhost. L’app iOS autorise le réseau local.

Au premier envoi, une notice explique ce qui part : totaux agrégés seulement, ou aussi les libellés (nécessaires à la catégorisation). Les propositions de catégories ne sont jamais appliquées automatiquement : vous les acceptez une par une, par référent, ou toutes, avec possibilité d’annuler.

## Utilisation locale

1. Téléchargez le fichier [`index.html`](index.html).
2. Ouvrez-le dans votre navigateur (double-clic suffit, aucun serveur ni installation).
3. Vos données restent dans ce navigateur. Pensez à exporter régulièrement une sauvegarde JSON.

## Confidentialité

Les données restent **locales**, dans le `localStorage` de votre navigateur. Aucun serveur de l’éditeur n’est contacté. L’assistant IA, s’il est activé, envoie uniquement au fournisseur que vous avez choisi (DashScope ou votre Ollama) le résumé ou les libellés que vous avez acceptés. Pour changer d’appareil, utilisez l’export JSON.

## Captures d’écran

Tableau de bord :

![Tableau de bord](docs/screenshot-dashboard.png)

Suivi de l’épargne :

![Suivi de l’épargne](docs/screenshot-epargne.png)

Calculatrice de projection :

![Calculatrice](docs/screenshot-calculatrice.png)

## Licence

Distribué sous licence [MIT](LICENSE). Copyright © 2026 Ahmed Khaldi.

## Contributions

Les contributions sont les bienvenues : issues, suggestions et pull requests.

---

## English

**Mon Budget** is a self-contained personal budget web app (French UI, EUR). You enter income and expenses yourself — there is no bank connection.

**[Try it online](https://khaldiahmed91-cyber.github.io/Mon-Budget/)** or download [`index.html`](index.html) and open it in a browser. Features include monthly and yearly recurrences with optional end dates, categories and subcategories, monthly budgets, a multi-year savings tracker, an N-year projection calculator, a local bank-statement importer (CSV, XLSX, OFX, QIF) with internal-transfer detection, an optional Qwen assistant (DashScope or local Ollama, off by default), JSON/CSV export, and dark mode.

Budget data stays in your browser’s `localStorage`. Nothing is sent to the publisher. If you enable the optional assistant, a summary (or transaction labels, if you agree) is sent only to the provider you chose. Licensed under the [MIT License](LICENSE). Contributions are welcome.
