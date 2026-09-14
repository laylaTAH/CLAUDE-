# Mon Agent Platform

Plateforme d'agents IA basée sur le Claude Agent SDK, pilotable avec Claude Code.

## Démarrage

```bash
cp .env.example .env
# renseigner ANTHROPIC_API_KEY dans .env

npm install
npm run dev -- "ta requête ici"
```

## Structure

```
.
├── CLAUDE.md                   # Instructions lues par Claude Code
├── memoire.md                  # Contexte persistant du projet
├── .claude/
│   ├── agents/                 # Sous-agents (mode CLI, fichiers .md)
│   │   ├── researcher.md
│   │   └── code-reviewer.md
│   ├── skills/                 # Savoir-faire réutilisables
│   │   └── synthese-reunion/
│   │       ├── SKILL.md
│   │       └── references/
│   └── settings.json           # Permissions Claude Code
├── src/
│   ├── index.ts                # Orchestrateur principal (query())
│   └── agents.config.ts        # Sous-agents (mode SDK, programmatique)
├── .env.example
└── package.json
```

## Ajouter un agent

- **Mode CLI (Claude Code)** : créer un fichier dans `.claude/agents/nom.md` avec le frontmatter `name`, `description`, `tools`, `model`.
- **Mode SDK (code)** : ajouter une entrée dans `src/agents.config.ts`.

Les deux peuvent coexister ; une définition dans `agents.config.ts` prend le dessus sur un fichier `.md` de même nom.

## Ajouter une skill

Créer `.claude/skills/nom-skill/SKILL.md` avec un frontmatter `name` + `description` (la description doit indiquer clairement quand l'utiliser — c'est elle que Claude lit pour décider de charger la skill). Ajouter des fichiers dans `scripts/`, `references/` ou `assets/` si la skill a besoin de ressources supplémentaires.

Une skill est disponible pour tous les agents du projet, contrairement à un sous-agent qui a son propre contexte isolé.
