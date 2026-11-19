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
- **Import de relevé bancaire** (CSV, Excel .xlsx, OFX/QFX, QIF), entièrement local
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

## Utilisation locale

1. Téléchargez le fichier [`index.html`](index.html).
2. Ouvrez-le dans votre navigateur (double-clic suffit, aucun serveur ni installation).
3. Vos données restent dans ce navigateur. Pensez à exporter régulièrement une sauvegarde JSON.

## Confidentialité

Toutes les données restent **100 % locales**, dans le `localStorage` de votre navigateur. Aucun serveur n’est contacté, aucune donnée n’est envoyée ailleurs. Pour changer d’appareil, utilisez l’export JSON.

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

**[Try it online](https://khaldiahmed91-cyber.github.io/Mon-Budget/)** or download [`index.html`](index.html) and open it in a browser. Features include monthly and yearly recurrences with optional end dates, categories and subcategories, monthly budgets, a multi-year savings tracker, an N-year projection calculator, a local bank-statement importer (CSV, XLSX, OFX, QIF), JSON/CSV export, and dark mode.

All data stays in your browser’s `localStorage`. Nothing is sent to a server. Licensed under the [MIT License](LICENSE). Contributions are welcome.
