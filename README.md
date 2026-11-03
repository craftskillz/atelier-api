# atelier-api

**Ce dépôt est un exemple pédagogique. Sa branche `feature/orders-list` contient des défauts volontaires : ne réutilisez pas ce code.**

C'est une petite API de commandes fictive, sans couche HTTP ni dépendance. Elle sert de terrain d'essai à la skill de revue de code [`review-code`](https://github.com/craftskillz/skill-code-review).

- `main` : la consultation des commandes.
- `feature/orders-list` : la liste paginée, le résumé, la facture et la remise. Les tests de cette branche passent malgré ses défauts.

Le contrat que le code doit respecter se trouve dans [`references/api.md`](https://github.com/craftskillz/skill-code-review/blob/main/skills/review-code/references/api.md). Vous pouvez aussi [comparer les deux branches](https://github.com/craftskillz/atelier-api/compare/main...feature/orders-list) directement sur GitHub.

## Lancer les tests

Node.js suffit, sans installation :

```bash
npm test
```

## Essayer la skill

Il vous faut Claude Code, Node.js, Python 3 et Git. Une revue consomme des requêtes, et ses résultats varient d'une exécution à l'autre.

```bash
git clone https://github.com/craftskillz/atelier-api.git
cd atelier-api
git branch feature/orders-list origin/feature/orders-list

npx skills@latest add craftskillz/skill-code-review --skill review-code --agent claude-code
python3 .claude/skills/review-code/scripts/install_agents.py
claude
```

Acceptez la confiance du dossier, puis lancez :

```text
/review-code main feature/orders-list
```

La skill exécute le code et les tests de la branche relue. Elle écrit ses corrections sur une branche `review-fixes/…` et son rapport dans `review-reports/`, sans modifier `feature/orders-list` ni rien pousser.
