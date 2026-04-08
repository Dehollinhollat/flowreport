# 📋 Méthodologie — FlowReport

## 1. Contexte et objectif

Ce projet est né d'un constat simple : dans les ESN, la production
de rapports d'activité hebdomadaires est une tâche répétitive et
chronophage. L'objectif était de concevoir un système automatisé
capable de remplacer ce processus manuel de bout en bout.

## 2. Choix techniques et justifications

### Pourquoi n8n plutôt que Make ?
n8n est open-source, auto-hébergeable et très valorisé dans les ESN
et cabinets de conseil. Il permet une logique plus fine via les Code
Nodes (JavaScript natif), ce qui était nécessaire pour le calcul des
KPIs. Make aurait été plus rapide à prendre en main mais moins
démonstratif techniquement.

### Pourquoi l'API Claude ?
Claude produit des analyses narratives cohérentes et structurées,
adaptées à un contexte professionnel. Le modèle Haiku a été choisi
pour son rapport qualité/coût optimal sur des tâches de génération
de rapports.

### Pourquoi Google Sheets comme source de données ?
C'est l'outil de saisie le plus répandu dans les équipes ESN. Le
connecteur natif n8n évite tout développement supplémentaire et
rend le système accessible à des non-techniciens.

### Pourquoi un rapport en HTML ?
Un rapport en texte brut est illisible dans un email. Le HTML permet
une mise en forme visuelle (cartes KPIs colorées, tableaux) qui 
améliore la lisibilité et l'impact pour le manager destinataire.

## 3. Architecture du pipeline

### Google Sheets → Schedule Trigger → Code Node (KPIs) → HTTP Request (Claude API) → Gmail

Chaque nœud a une responsabilité unique — principe de séparation
des responsabilités appliqué à l'automatisation.

## 4. Difficultés rencontrées

| Difficulté | Solution |
|---|---|
| Expressions `{{ }}` invalides en JSON dans n8n | Construction du requestBody directement dans le Code Node |
| Gmail n'affichait pas le HTML | Utilisation de `bgcolor` HTML natif plutôt que CSS inline |
| Rapport tronqué par Claude | Augmentation de `max_tokens` à 8192 |
| Clé API exposée dans le workflow.json | Remplacement par `VOTRE_CLE_API_ANTHROPIC` avant le commit |
| Erreur 403 Google OAuth | Ajout du compte comme testeur dans Google Cloud Console |

## 5. Sécurité

- La clé API Anthropic n'est jamais committée dans le repo
- Les credentials Google sont gérés via OAuth2 dans n8n
- Le workflow exporté contient un placeholder à remplacer

## 6. Améliorations possibles

- Filtrage dynamique par semaine courante
- Historisation automatique des KPIs dans un onglet Google Sheets
- Ajout d'un rapport individuel par consultant
- Déploiement n8n sur un serveur cloud (Railway, Render) pour
  une exécution sans PC allumé

## 7. Compétences développées

- Conception d'architecture Data/IA de bout en bout
- Intégration d'API REST dans un workflow no-code
- Prompt engineering appliqué à un cas métier réel
- Sécurisation des credentials dans un projet IA
- Documentation technique professionnelle
