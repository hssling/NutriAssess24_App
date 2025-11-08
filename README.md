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
