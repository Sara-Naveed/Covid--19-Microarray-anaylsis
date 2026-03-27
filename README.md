# COVID-19 Drug Target Identification via Network Pharmacology

> A computational pipeline to identify potential drug targets and hub genes for COVID-19 using ligand screening, ADMET analysis, protein interaction networks, and Cytoscape-based hub gene identification.

---

## Overview

This project applies a **network pharmacology approach** to identify key therapeutic targets for COVID-19. Starting from disease-associated genes and known antiviral ligands, the pipeline integrates multiple bioinformatics databases and tools to narrow down the most biologically significant hub genes — potential candidates for drug development.

---

## Workflow

```
Disease Gene Selection (GeneCards)
        ↓
Ligand Selection from Literature (12 compounds)
        ↓
SMILES Retrieval (PubChem)
        ↓
ADMET Filtering (SwissADME)
        ↓
Target Prediction (SwissTargetPrediction)
        ↓
Venn Diagram → 519 Common Genes
        ↓
Functional Enrichment (DAVID)
        ↓
Protein-Protein Interaction Network (STRING)
        ↓
Hub Gene Identification (Cytoscape + CytoHubba)
```

---

## Tools & Databases Used

| Tool / Database | Purpose |
|----------------|---------|
| [GeneCards](https://www.genecards.org/) | Disease-associated gene retrieval |
| [PubChem](https://pubchem.ncbi.nlm.nih.gov/) | SMILES structure retrieval |
| [SwissADME](http://www.swissadme.ch/) | ADMET properties & drug-likeness |
| [SwissTargetPrediction](http://www.swisstargetprediction.ch/) | Ligand-target prediction |
| [GeneVenn](http://genevenn.sourceforge.net/) | Common gene identification |
| [DAVID](https://david.ncifcrf.gov/) | GO & KEGG pathway enrichment |
| [STRING](https://string-db.org/) | Protein-protein interaction network |
| [Cytoscape](https://cytoscape.org/) + CytoHubba | Network visualization & hub gene ranking |

---

## Ligands Studied

12 ligands shortlisted from literature review based on known antiviral activity against COVID-19:

| Ligand | Target |
|--------|--------|
| gp120 | Viral entry protein |
| CXCR4 antagonist | Chemokine receptor |
| Nevirapine | Reverse transcriptase |
| Ritonavir | HIV/COVID protease |
| Lopinavir | Protease inhibitor |
| Atazanavir | Protease inhibitor |
| Glycosphingolipid | Membrane component |
| CCR3 antagonist | Chemokine receptor |
| CCR8 antagonist | Chemokine receptor |
| CCR1 antagonist | Chemokine receptor |

SMILES structures retrieved from PubChem for all 12 compounds.

---

## Key Results

- **519 common genes** identified between COVID-19 disease genes and ligand-predicted targets via Venn diagram analysis
- **Biological processes, KEGG pathways, and Gene Ontology** terms analyzed via DAVID database
- **Protein-protein interaction network** constructed using STRING (organism: *Homo sapiens*)
- **Top 10 hub genes** identified using CytoHubba plugin in Cytoscape — these represent the most highly connected and biologically significant nodes in the network

---

## Pipeline Steps

### 1. Disease Gene Collection
- Searched COVID-19 on GeneCards
- Exported disease-associated genes to CSV
- Removed duplicate entries

### 2. Ligand Selection & SMILES Retrieval
- Reviewed literature to identify 12 relevant ligands
- Retrieved canonical SMILES for each from PubChem

### 3. ADMET Analysis (SwissADME)
- Input all SMILES into SwissADME
- Evaluated drug-likeness, bioavailability, and pharmacokinetic properties
- Exported results as CSV

### 4. Target Prediction (SwissTargetPrediction)
- Submitted each SMILES individually
- Downloaded predicted targets as separate CSVs
- Merged into one combined target list

### 5. Common Gene Identification
- Used GeneVenn to find overlap between disease genes and predicted targets
- Result: **519 shared genes**

### 6. Functional Enrichment (DAVID)
- Input 519 common genes into DAVID
- Extracted Biological Process, KEGG Pathway, and Gene Ontology annotations
- Saved each category as a separate Excel sheet

### 7. Network Construction
- Built ligand-target interaction file (CSV: molecule ↔ target)
- Imported into Cytoscape via File → Import Network from File
- Fetched PPI data from STRING database (Homo sapiens)
- Applied probability threshold filtering

### 8. Hub Gene Identification
- Used CytoHubba plugin
- Selected Top 10 hub genes
- Exported network visualization as PNG

---

## Requirements

- Cytoscape 3.x + Java (same directory)
- CytoHubba plugin
- Microsoft Excel / Google Sheets
- Internet access for online tools (SwissADME, SwissTargetPrediction, STRING, DAVID)

---

## Project Structure

```
covid19-network-pharmacology/
├── data/
│   ├── disease_genes.csv          # GeneCards COVID-19 genes
│   ├── ligand_smiles.csv          # 12 ligands with SMILES
│   ├── swissadme_results.csv      # ADMET properties
│   ├── target_predictions/        # Per-ligand SwissTargetPrediction CSVs
│   ├── common_genes_519.csv       # Venn diagram output
│   ├── david_enrichment/          # GO, KEGG, Biological process sheets
│   └── string_ppi.csv             # STRING interaction data
├── networks/
│   ├── ligand_target_network.csv  # Cytoscape input
│   └── hub_genes_network.png      # CytoHubba top 10 output
└── README.md
```

---

## Skills Demonstrated

- Network pharmacology & computational drug discovery
- Multi-database integration (GeneCards, PubChem, STRING, DAVID)
- ADMET property evaluation
- Protein-protein interaction network analysis
- Biological pathway enrichment analysis
- Cytoscape network visualization

---

## Author

**Sara Naveed**  
Bioinformatics | Computational Drug Discovery | ML in Biology  
GitHub: [Sara-Naveed](https://github.com/Sara-Naveed)
