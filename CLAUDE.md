# CLAUDE.md — Instructions du projet

Ce fichier est lu automatiquement par Claude Code au démarrage de chaque session dans ce dossier.

## Contexte
Plateforme d'agents IA construite avec le Claude Agent SDK (TypeScript).
Voir `memoire.md` pour le contexte persistant (décisions, état d'avancement).

## Stack
- Runtime : Node.js
- SDK : `@anthropic-ai/claude-agent-sdk`
- Langage : TypeScript
- Modèle par défaut : `claude-sonnet-4-6` (voir `.env`)

## Conventions
- Un sous-agent = un fichier dans `.claude/agents/` (nom, description, tools, model)
- Une skill = un dossier dans `.claude/skills/<nom>/SKILL.md` (savoir-faire réutilisable, chargé à la demande par n'importe quel agent)
- Les tools custom vont dans `src/tools/`
- Ne jamais committer `.env` (voir `.gitignore`)
- Avant toute modification structurante, mettre à jour `memoire.md`

## Agents vs Skills
- Agent = une identité avec ses propres outils et son propre contexte, invoquée pour une tâche
- Skill = une procédure/expertise que Claude (agent principal ou sous-agent) charge à la demande, sans changer de contexte
- Une skill peut être utilisée par plusieurs agents différents

## Commandes utiles
- `npm install` — installer les dépendances
- `npm run dev` — lancer l'orchestrateur en local
- `/install-github-app` — connecter GitHub Actions (optionnel, plus tard)

## Ce que Claude Code doit faire par défaut
- Lire `memoire.md` avant de proposer des changements d'architecture
- Proposer un sous-agent dédié (`.claude/agents/*.md`) plutôt que d'alourdir l'agent principal
- Documenter toute nouvelle variable d'environnement dans `.env.example`
