NutriAssess24 Privacy Policy
Effective date: December 6, 2025

This Privacy Policy explains how NutriAssess24 treats information when you install or use the NutriAssess24 Android application and related materials. NutriAssess24 is an educational nutritional assessment tool that runs entirely on your device, designed to be safe for all age groups. There is no advertising, no required payments, and no premium tiers; the app is free to use for anyone who needs an offline nutrition reference. It does not collect, transmit, or retain any personal information outside your device. By downloading or using NutriAssess24 you acknowledge that you accept this policy. you accept this policy.

Information we collect
NutriAssess24 does not collect or transmit any personal or usage information to its creator or any external server. All data you enter for assessments (such as anthropometry, dietary intake, notes, or references) remains encrypted and stored only on your device. The app functions offline, does not sync to the cloud, and never shares information with third parties.

How we use information
Because we do not collect or transmit information externally, we do not use it outside of the app. All computation, personalization, and data exports (CSV/PDF) happen locally on the device. You remain in full control of your entered data, and nothing is shared or used beyond your own device.

Sharing and disclosure
NutriAssess24 does not share or transmit data with any third party. There is no advertising, tracking, or profiling in the app. Because nothing leaves your device, there is no disclosure to service providers, governments, or other entities.

Data retention
All data stays on your device and is retained only until you delete it or uninstall the app. If you wish to fully delete the stored content, remove the app from your device or use the in-app delete options. There is no external backup or retention of your data.

Security
We implement reasonable security measures (encryption in transit, restricted access controls, and secure storage) to protect your data. However, no system is completely secure, so we cannot guarantee absolute protection and encourage you to safeguard your device.

Children’s privacy
NutriAssess24 is not directed at children under 13. If we learn that we have inadvertently collected personal information from a child younger than 13, we will delete it promptly.

Your choices
You control how the app works on your device. You can edit or delete any stored information directly inside the app and export assessments to CSV or PDF when needed. Because the app operates offline and has no account or authentication, there are no cookies, no advertising, and no required payments or subscriptions.

International data transfers
Because the application is distributed globally, your data may be transferred to, processed, and stored in countries outside your home country. We rely on legal mechanisms such as standard contractual clauses to help protect your rights.

Changes to this policy
We may update this Privacy Policy from time to time. When we do, we will revise the “Effective date” at the top and notify you through the app or other means.

Contact
If you have questions or want to exercise your privacy rights, please contact us at hssling@yahoo.com.

# NutriAssess24 v3 – IFCT + RDA + PDF

This build adds:
- CSV importer hooks for the official IFCT tables (`assets/ifct_full.csv` expected schema).
- Expanded RDA JSON structure (`assets/icmr_rda_full.json`).
- A working PDF export (Android PdfDocument) and improved CSV export.

How to wire real IFCT
1. Obtain the official IFCT 2017 CSV (respecting license) and map its columns to the schema in `assets/ifct_full.csv` header.
2. Place the file as `app/src/main/assets/ifct_full.csv`.
3. On app start (or from a settings action you add), call `IfctImporter.importFromAssets(context, NutriApp.db.openHelper.writableDatabase)` to overwrite the seed with the official values.

How to wire full ICMR RDA
1. Populate `assets/icmr_rda_full.json` with the complete age/sex/activity/physiological targets (ICMR‑NIN RDA 2020).
2. Load it using kotlinx.serialization and feed into `NutritionCalculator`.

PDF export
`PdfExporter.exportSummaryPdf(...)` writes an A4 PDF to app files. Replace with a Compose-to-PDF approach for richer layout if needed.

NOTE: Only minimal example rows are included to stay within fair use. Insert the official datasets yourself before production.
