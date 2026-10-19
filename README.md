# Nii Orchestrator

Préparer un projet complet, puis le réaliser progressivement : **un lot vérifié à la fois, avec un bilan avant de continuer**.

Nii Orchestrator aide à cadrer le produit, à rédiger un prompt d'implémentation pour une nouvelle session et à préparer le passage de relais vers un autre chat. Il s'inspire de [Feature Orchestrator](https://github.com/ski043/Skills/tree/main/skills/feature-orchestrator), avec une différence centrale : l'exécution s'arrête après chaque lot livré au lieu de poursuivre toute la feuille de route sans interruption.

## Installation

Prérequis : Node.js avec `npx`, un agent compatible avec les skills, et des outils de développement adaptés au projet à réaliser.

Pour une installation personnelle accessible dans plusieurs projets :

```bash
npx skills add RaNiiJohnson/nii-orchestrator --skill nii-orchestrator --global
```

Pour installer seulement dans le projet courant, exécuter depuis sa racine :

```bash
npx skills add RaNiiJohnson/nii-orchestrator --skill nii-orchestrator
```

Suivre les choix proposés par l'installateur pour l'agent concerné. Ouvrir ensuite une nouvelle session de l'agent pour qu'il découvre le skill.

Pour inspecter les fichiers avant installation :

```bash
git clone https://github.com/RaNiiJohnson/nii-orchestrator.git
```

Le skill complet se trouve dans `nii-orchestrator/`. Pour une installation manuelle personnelle dans Codex, copier ce dossier complet dans `~/.agents/skills/nii-orchestrator/`, références et métadonnées incluses. Ne pas écraser une installation existante contenant des modifications personnelles.

## Utilisation avec Codex

### Cadrer un projet

```text
$nii-orchestrator Cadre mon projet et prépare une réalisation par lots. Commençons par préciser les utilisateurs, les fonctions et les limites de la première version.
```

L'agent discute et inspecte les éléments existants ; il ne commence pas à modifier l'application pendant ce cadrage. Les propositions ne deviennent pas automatiquement des décisions validées.

### Préparer le prompt de réalisation

```text
$nii-orchestrator Les choix du produit sont arrêtés. Prépare le prompt complet avec arrêt après chaque lot prêt pour une PR.
```

Le skill demande les modèles et efforts souhaités pour les trois rôles de sous-agents. Si le message de compilation les précise déjà, il confirme les valeurs et poursuit sans redemander les mêmes informations.

| Rôle | Responsabilité |
| --- | --- |
| Lead | Agent principal de la session de réalisation ; conserve son modèle de lancement. |
| Implementer | Modifications bornées, tests et corrections confirmées. |
| Researcher | Documentation, exploration en lecture seule et vérifications d'API. |
| Reviewer | Revue indépendante en lecture seule, avec un contexte neuf. |

Les modèles ne sont pas imposés par le skill. Leur disponibilité et leurs réglages doivent être vérifiés dans l'environnement réel ; une substitution doit être annoncée et acceptée.

Copier le prompt produit dans une nouvelle session ouverte sur le bon dépôt. Cette session prépare la feuille de route complète, puis réalise uniquement le premier lot inachevé dont les dépendances sont satisfaites.

### Passer le relais

```text
$nii-orchestrator Prépare le passage de relais vers le prochain chat en vérifiant le dépôt, les tâches, les tests et l'état Git actuels.
```

Le passage de relais contient la mission suivante, les décisions, les documents utiles, les vérifications réellement effectuées, les fichiers non enregistrés et les blocages. Il peut servir dans le même chat ou dans un nouveau, sans reprendre toute la conversation.

## Ce qui se passe à chaque lot

1. Annonce de l'objectif, du périmètre et du résultat à essayer.
2. Réalisation avec des nouvelles aux jalons significatifs.
3. Vérifications et, pour les interfaces, observation et interaction dans le navigateur pendant le développement.
4. Revue indépendante, confirmation des problèmes et corrections ; au maximum deux cycles complets de revue et remédiation.
5. Mise à jour des documents du projet et bilan de livraison.
6. Arrêt avant le lot suivant, en attendant une demande explicite de continuer.

Un lot bloqué ou partiellement vérifié est présenté comme tel. L'agent ne doit pas le déclarer terminé pour avancer dans la feuille de route.

## Lots et pull requests

Un lot est un résultat cohérent et vérifiable. Une mission de sous-agent, un commit et une PR sont des objets distincts : le découpage dépend du projet réel.

Le bilan fournit le contenu de la PR proposée, les contrôles et l'état Git. Sans accès au dépôt distant, le lot peut être livré localement avec une proposition de PR.

**Dire « continue » autorise le prochain lot, pas un push, une ouverture de PR, une fusion ou un déploiement.** Ces actions externes demandent une autorisation applicable et distincte. Une PR ouverte n'autorise pas automatiquement le lot suivant.

## Compatibilité et limites

- Le dossier contient des instructions Markdown et des métadonnées d'invocation explicite pour Codex.
- Dans Claude Code ou un autre environnement compatible, utiliser le mécanisme natif d'invocation et vérifier les noms de modèles, les efforts et la disponibilité des sous-agents ; les identifiants Codex ne sont pas des identifiants portables.
- Le skill prépare des consignes : ce n'est pas un service qui surveille les chats ni un moteur qui crée des PR automatiquement.
- Les modes de l'environnement, ses autorisations et ses limites de concurrence restent applicables.
- Aucun compte, secret, abonnement ou outil externe n'est créé par l'installation de ce skill.

## Fichiers

- [SKILL.md](SKILL.md) : instructions principales.
- [Modèles des sous-agents](references/model-roster.md) : choix et contraintes de plateforme.
- [Contrat d'exécution progressive](references/execution-prompt-contract.md) : structure des prompts, checkpoints et passages de relais.

## Licence et origine

Distribué sous la [licence MIT du dépôt](LICENSE).

Nii Orchestrator est une adaptation de Feature Orchestrator. La notice existante de Jan Marshal est conservée dans la licence, avec une attribution distincte aux ajouts Nii Orchestrator de RaNiiJohnson.
