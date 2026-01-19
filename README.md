# Kadastrale Datapijplijn – DuckDB & DBT Core

Deze repository bevat de volledige documentatie van een lokaal uitgevoerde ELT‑datapijplijn voor het verwerken van Nederlandse kadastrale data via de PDOK API. De pipeline combineert Python, DuckDB en DBT Core om een snelle, transparante en schaalbare workflow te realiseren zonder afhankelijkheid van cloud‑infrastructuur.

---

##  Samenvatting

In dit project is een complete lokale datapijplijn ontworpen en geïmplementeerd voor het ophalen, opslaan, transformeren en documenteren van kadastrale data.  
De workflow bestaat uit:

- **Extract & Load (Python)** – ophalen van data via de PDOK API en laden in DuckDB  
- **Transform (DBT Core)** – bouwen van staging‑ en mart‑modellen  
- **Data‑kwaliteitstests** – not_null, unique en schema‑validatie  
- **Automatische documentatie** – via `dbt docs generate`  
- **Troubleshooting‑gids** – voor veelvoorkomende fouten en oplossingen  

De oplossing is volledig lokaal, kostenefficiënt, modulair en eenvoudig uitbreidbaar.

---

##  Doelstellingen

- Ophalen van kadastrale data via de PDOK API  
- Laden van ruwe data in DuckDB  
- Transformeren naar analyseklare tabellen met DBT  
- Toevoegen van documentatie en datatests  
- Bouwen van staging‑ en mart‑modellen  
- Iteratieve ontwikkeling met Git  
- Uitvoeren, testen en documenteren van de volledige pipeline  

---

## Tools & Technologieën

| Tool | Rol in de pipeline | Waarom gekozen |
|------|---------------------|----------------|
| **PDOK API** | Bronsysteem | Open, actueel, betrouwbaar |
| **Python** | Extract & Load | Flexibel, ideaal voor API‑integraties |
| **DuckDB** | Opslag & analyse | Supersnel, lokaal, zero‑config |
| **DBT Core** | Transformatie, testen, documentatie | SQL‑first, schaalbaar, professioneel |

---

## Architectuur

De pipeline volgt het **ELT‑principe**:

1. **Extract** – Data ophalen via PDOK API  
2. **Load** – Opslaan in DuckDB  
3. **Transform** – DBT‑modellen bouwen (staging & marts)

**Lagen in de architectuur:**

- **Data Source** – PDOK API  
- **Ingestion Layer** – Python scripts  
- **Raw Data Layer** – DuckDB  
- **Transformation Layer** – DBT Core  
- **Consumption Layer** – Analyse, rapportage, visualisatie  

---

## Workflow Overzicht

1. Download data via PDOK API  
2. Laad data in DuckDB  
3. Initialiseer DBT‑project  
4. Bouw staging‑modellen (`stg_`)  
5. Bouw mart‑modellen (`mrt_`)  
6. Voer tests uit  
7. Genereer documentatie  
8. Iteratief verbeteren via Git  

---

##  Installatie & Setup

### 1. Vereiste tools

- Python  
- Git  
- DuckDB CLI  
- DBT Core + DuckDB adapter  

### 2. DBT configuratie (profiles.yml)

```yaml
mijn_dbt_project:
  target: dev
  outputs:
    dev:
      type: duckdb
      path: C:/Users/BongyuPaschal/dbt/dev.duckdb
      threads: 1
