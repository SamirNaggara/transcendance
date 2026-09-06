# ft_transcendence

Un Pong multijoueur en temps réel dans le navigateur, avec chat, profils et double authentification. Projet final du tronc commun de 42 Paris, réalisé à cinq entre novembre 2023 et janvier 2024, 336 commits et 110 merges.

Le dépôt d'origine est celui de l'équipe : [dbelpaum/ft_transcendence](https://github.com/dbelpaum/ft_transcendence). Celui-ci en est une copie complète, avec tout l'historique, publiée sur mon compte pour garder une trace de ma part du travail.

## Ce qui est implémenté

- **Connexion** par OAuth 42, sessions JWT, double authentification TOTP (QR code à scanner avec une application type Google Authenticator)
- **Jeu** : Pong à deux en temps réel via WebSocket, lobby, matchmaking, invitation à jouer depuis le chat, prise en compte des pseudos, historique et scores
- **Chat** : salons publics, privés et protégés par mot de passe, messages privés, administrateurs, kick, ban et mute, blocage d'utilisateurs
- **Social** : profils, amis, liste des utilisateurs, statut en ligne
- **Déploiement** : tout en conteneurs Docker, une seule commande pour lancer front, back et base de données, configuration de production avec TLS

## Stack

- Front : React 18, TypeScript, socket.io-client
- Back : NestJS 10, Prisma 5, PostgreSQL, socket.io, Passport JWT, otplib, bcrypt
- Infra : Docker Compose, nginx

## Ma part

- Le chat de bout en bout : gateway WebSocket côté NestJS, salons, rôles d'administrateur, ban et mute par identifiant, blocage, messages privés, interface React
- La double authentification (QR code et vérification TOTP)
- La sécurisation des requêtes internes et des routes de l'API
- La mise en production (Dockerfiles de prod, variables d'environnement) et une partie du responsive du jeu et du lobby

## Lancer le projet

```bash
cp example.env .env   # puis remplir les variables (clés OAuth 42, base de données)
docker compose up --build
```

- Front : http://localhost:3000
- API : http://localhost:4000
- Prisma Studio : http://localhost:5555

Les certificats dans `src/*/conf` sont auto-signés, pour le développement uniquement.

## Équipe

dbelpaum, Yamisan0, idris, lebackor et moi.
