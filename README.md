# 📋 Application TODO Multi-tier avec Docker Compose

Ce projet démontre une architecture web multi-tier conteneurisée avec Docker Compose, comprenant un frontend, un backend et une base de données.

## 🏗️ Architecture

### Services
- **Frontend**: Application Next.js 15 avec TypeScript et Tailwind CSS
- **Backend**: API REST avec Next.js API routes
- **Base de données**: PostgreSQL avec persistance des données
- **Reverse Proxy**: Nginx pour la gestion des requêtes

### Technologies
- **Framework**: Next.js 15 avec App Router
- **Langage**: TypeScript 5
- **Style**: Tailwind CSS avec shadcn/ui
- **Base de données**: PostgreSQL + Prisma ORM
- **Conteneurisation**: Docker + Docker Compose
- **Proxy**: Nginx

## 🚀 Démarrage rapide

### Prérequis
- Docker installé sur votre machine
- Docker Compose installé

### Installation et déploiement

1. **Cloner le projet**
   ```bash
   git clone <repository-url>
   cd todo-multi-tier
   ```

2. **Déployer avec Docker Compose**
   ```bash
   docker-compose up --build
   ```
   
   Ou utiliser le script de déploiement :
   ```bash
   ./deploy.sh
   ```

3. **Accéder à l'application**
   - Frontend via Nginx: http://localhost:80
   - Application directe: http://localhost:3000
   - API: http://localhost:3000/api/todos

## 📁 Structure du projet

```
todo-multi-tier/
├── src/
│   ├── app/
│   │   ├── api/todos/          # API routes (backend)
│   │   ├── page.tsx            # Frontend principal
│   │   └── layout.tsx          # Layout de l'application
│   ├── components/ui/          # Composants shadcn/ui
│   └── lib/
│       ├── db.ts               # Configuration Prisma
│       └── utils.ts            # Utilitaires
├── prisma/
│   ├── schema.prisma           # Schéma de la base de données
│   └── migrations/             # Migrations Prisma
├── Dockerfile                  # Configuration Docker
├── docker-compose.yml          # Orchestration des services
├── nginx.conf                  # Configuration Nginx
└── package.json                # Dépendances Node.js
```

## 🔧 Fonctionnalités

### Gestion des TODOs
- ✅ Créer une nouvelle tâche
- ✅ Afficher la liste des tâches
- ✅ Modifier une tâche existante
- ✅ Supprimer une tâche
- ✅ Marquer une tâche comme complétée
- ✅ Définir la priorité (Basse, Moyenne, Haute)

### API Endpoints
- `GET /api/todos` - Récupérer toutes les tâches
- `POST /api/todos` - Créer une nouvelle tâche
- `PUT /api/todos/[id]` - Mettre à jour une tâche
- `DELETE /api/todos/[id]` - Supprimer une tâche

## 🐳 Services Docker

### Service app (Next.js)
- Construit l'application Next.js en mode production
- Expose le port 3000
- Utilise une image Node.js Alpine optimisée

### Service db (PostgreSQL)
- Base de données PostgreSQL 15
- Persistance des données via volume
- Configuration par variables d'environnement

### Service nginx (Reverse Proxy)
- Proxy inverse Nginx
- Expose le port 80
- Route les requêtes vers l'application Next.js

## 🛠️ Commandes utiles

### Docker Compose
```bash
# Démarrer tous les services
docker-compose up -d

# Arrêter tous les services
docker-compose down

# Voir les logs
docker-compose logs -f

# Reconstruire les images
docker-compose build

# Voir l'état des services
docker-compose ps
```

### Développement
```bash
# Installer les dépendances
npm install

# Démarrer le serveur de développement
npm run dev

# Générer le client Prisma
npx prisma generate

# Appliquer les migrations
npm run db:push
```

## 📊 Architecture multi-tier

### Tier 1 - Frontend (Présentation)
- Interface utilisateur avec Next.js et shadcn/ui
- Communication avec le backend via API REST
- Gestion de l'état côté client

### Tier 2 - Backend (Logique métier)
- API REST avec Next.js API routes
- Validation des données
- Logique métier
- Communication avec la base de données

### Tier 3 - Base de données (Stockage)
- PostgreSQL pour la persistance des données
- Prisma ORM pour l'accès aux données
- Volumes pour la persistance

## 🔒 Sécurité

- Utilisateur non-root dans les conteneurs
- Variables d'environnement pour les données sensibles
- Isolation des services via réseaux Docker
- Proxy inverse pour la gestion des requêtes

## 📈 Monitoring

### Logs
- Logs de l'application: `docker-compose logs app`
- Logs de la base de données: `docker-compose logs db`
- Logs de Nginx: `docker-compose logs nginx`

### Performance
- Images optimisées avec multi-stage builds
- Cache Docker pour les builds rapides
- Volume persistant pour les données

## 🧪 Tests

### Tester l'API
```bash
# Récupérer tous les todos
curl http://localhost:3000/api/todos

# Créer un nouveau todo
curl -X POST http://localhost:3000/api/todos \
  -H "Content-Type: application/json" \
  -d '{"title":"Test todo","description":"Description test","priority":"HIGH"}'
```

## 📝 Développement futur

- [ ] Ajouter l'authentification des utilisateurs
- [ ] Implémenter le temps réel avec WebSocket
- [ ] Ajouter des tests automatisés
- [ ] Monitoring avec Prometheus/Grafana
- [ ] CI/CD avec GitHub Actions

## 📚 Documentation

- [Next.js Documentation](https://nextjs.org/docs)
- [Docker Documentation](https://docs.docker.com/)
- [Docker Compose Documentation](https://docs.docker.com/compose/)
- [Prisma Documentation](https://www.prisma.io/docs/)
- [shadcn/ui Documentation](https://ui.shadcn.com/)

---

🎯 **Objectif pédagogique**: Ce projet démontre une architecture web moderne multi-tier, utilisant les meilleures pratiques de conteneurisation et d'orchestration avec Docker Compose.
