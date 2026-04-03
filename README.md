# 🟠 FlowReport — Pipeline d'automatisation IA de rapports de performance

> Projet personnel réalisé pour dévélopper mes compétences dans la Data et l'IA

## 📌 Problématique

Dans les ESN, les managers passent 2 à 3h par semaine à consolider
les données d'activité de leurs équipes et rédiger des rapports manuellement.
FlowReport automatise ce cycle de bout en bout.

## ⚙️ Architecture du pipeline
```
[Google Sheets] → [n8n] → [Calcul KPIs] → [API Claude] → [Rapport email]
```

## 🚀 Fonctionnalités

- Lecture automatique des données d'activité depuis Google Sheets
- Calcul des KPIs : taux de complétion, heures par consultant, tâches bloquées
- Génération d'un rapport narratif par IA (Claude API)
- Envoi automatique par email chaque lundi à 8h

## 🛠️ Stack technique

| Outil | Rôle |
|---|---|
| n8n | Orchestration du pipeline |
| Google Sheets | Source de données |
| API Claude (Anthropic) | Génération du rapport IA |
| Gmail | Envoi automatique |

## 📂 Structure du repo
```
flowreport/
│
├── data/
│   └── sample_data.csv          ← 80 tâches, 4 consultants, 4 semaines
│
├── n8n/
│   └── workflow.json            ← Pipeline exporté (clé API remplacée par VOTRE_CLE_API)
│
├── prompts/
│   └── report_prompt.txt        ← Prompt Claude documenté et versionné
│
├── output/
│   └── sample_report.html       ← Rapport HTML final généré par l'IA
│
├── docs/
│   ├── pipeline_n8n.png         ← Capture du workflow n8n
│   └── rapport_email.png        ← Capture du rendu email HTML
│
└── README.md                    ← Documentation pro + architecture + screenshots
```

## 🖼️ Aperçu

### Pipeline n8n
![Pipeline n8n](docs/pipeline_n8n.png)

### Rapport généré par IA
![Rapport email](docs/rapport_email.png)

Voir [`output/sample_report.txt`](output/sample_report.txt)

## ⚠️ Sécurité

Ne jamais committer de clé API.
Remplacer `VOTRE_CLE_API_ANTHROPIC` dans `n8n/workflow.json`
par votre propre clé via les credentials n8n.

## 👤 Auteur

**Déhollin HOLLAT** — Chef de Projet Data IA  
Formation MBA Big Data & IA
