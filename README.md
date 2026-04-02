# 🟠 FlowReport — Pipeline d'automatisation IA de rapports de performance

> Projet personnel réalisé dans le cadre d'une formation MBA Big Data & IA

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
├── data/
│   └── sample_data.csv       ← Données simulées (80 tâches, 4 consultants)
├── n8n/
│   └── workflow.json         ← Export du workflow n8n (clé API à configurer)
├── prompts/
│   └── report_prompt.txt     ← Prompt Claude documenté
├── output/
│   └── sample_report.txt     ← Exemple de rapport généré
└── README.md
```

## 📊 Exemple de rapport généré

Voir [`output/sample_report.txt`](output/sample_report.txt)

## ⚠️ Sécurité

Ne jamais committer de clé API.
Remplacer `VOTRE_CLE_API_ANTHROPIC` dans `n8n/workflow.json`
par votre propre clé via les credentials n8n.

## 👤 Auteur

**Déhollin HOLLAT** — Chef de Projet Data IA  
Formation MBA Big Data & IA
