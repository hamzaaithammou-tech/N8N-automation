# N8N Automation Workflows
 
Bienvenue dans mon repository N8N Automation ! 🚀 Ce projet contient une collection de workflows d'automation sophistiqués utilisant n8n pour intégrer différentes applications et APIs.
 
## 📋 Table des matières
 
- [À propos](#à-propos)
- [Workflows inclus](#workflows-inclus)
- [Prérequis](#prérequis)
- [Installation](#installation)
- [Configuration](#configuration)
- [Utilisation](#utilisation)
- [Architecture](#architecture)
- [Support](#support)
## 🎯 À propos
 
Ce repository contient des workflows n8n automatisés conçus pour :
- Traiter les soumissions de formulaires
- Filtrer et traiter les données
- Extraire des informations via des APIs
- Intégrer Anthropic Chat pour l'intelligence artificielle
- Insérer des données dans des bases de données
- Envoyer des messages automatiques
- Mettre à jour des lignes de données
Les workflows utilisent une approche modulaire avec des conditions logiques (if/else) et une gestion avancée des données.
 
## 📦 Workflows inclus
 
### 1. **Form Submission & Processing Workflow**
Workflow complet de traitement de soumissions de formulaires avec les étapes suivantes :
- Déclencheur : Soumission de formulaire
- Filtrage des données
- Extraction d'informations
- Branchement conditionnel (true/false/manual)
- Intégration avec Anthropic Chat Model
- Insertion de lignes en base de données
- Envoi de messages
**Cas d'usage** : Automatiser le traitement des demandes client, des inscriptions ou des enquêtes.
 
### 2. **AI-Powered Chat Workflow**
Workflow déclenchant une action automatisée au reçu d'un message chat :
- Déclencheur : Réception d'un message chat
- Intégration Anthropic Chat Model
- Gestion de la mémoire simple
- Récupération des données (fetch Q&A)
- Insertion de lignes dans une base de données
- Réponses automatiques
**Cas d'usage** : Chatbot intelligent avec mémoire persistante et recherche de base de données.
 
### 3. **Advanced Data Processing Workflow**
Workflow avec logique conditionnelle avancée :
- Conditions multiples (if/then/else)
- Instructions manuelles comme option
- Boucles itératives
- Traitement en parallèle
**Cas d'usage** : Workflows complexes nécessitant une logique métier sophistiquée.
 
## ✅ Prérequis
 
- **n8n** (auto-hébergé ou cloud) - [Installation](https://docs.n8n.io/getting-started/)
- **Compte Anthropic** - Pour utiliser l'API Claude
- **Bases de données supportées** : 
  - PostgreSQL
  - MySQL
  - MongoDB
  - Google Sheets (via API)
  - Autres intégrations n8n
- **Node.js** (si auto-hébergé) - v14.0.0 ou supérieur
## 🚀 Installation
 
### Étape 1 : Cloner le repository
 
```bash
git clone https://github.com/hamzaaithammou-tech/N8N-automation.git
cd N8N-automation
```
 
### Étape 2 : Configurer n8n
 
Si vous utilisez n8n auto-hébergé :
 
```bash
npm install -g n8n
n8n start
```
 
Puis accédez à `http://localhost:5678`
 
### Étape 3 : Importer les workflows
 
1. Dans l'interface n8n, allez à **Workflows**
2. Cliquez sur **Import from file** ou **Import from URL**
3. Sélectionnez les fichiers JSON des workflows depuis ce repository
4. Les workflows seront importés avec leur configuration
## ⚙️ Configuration
 
### Variables d'environnement
 
Créez un fichier `.env` à la racine du projet :
 
```env
# Anthropic API
ANTHROPIC_API_KEY=your_api_key_here
 
# Base de données
DB_HOST=localhost
DB_PORT=5432
DB_NAME=automation_db
DB_USER=postgres
DB_PASSWORD=your_password
 
# Webhook (si applicable)
WEBHOOK_URL=https://your-domain.com/webhook
 
# Paramètres n8n
N8N_WEBHOOK_TUNNEL_URL=https://your-domain.com
```
 
### Configuration des nœuds
 
Chaque workflow nécessite de configurer :
 
1. **Anthropic Chat Model** : 
   - Ajouter votre clé API Anthropic
   - Configurer le modèle (claude-opus, claude-sonnet, etc.)
2. **Base de données** :
   - Configurer la connexion à votre DB
   - Modifier les requêtes SQL selon votre schéma
3. **Déclencheurs** :
   - Configurer les webhooks ou les triggers applicatifs
   - Ajuster les filtres si nécessaire
## 📖 Utilisation
 
### Déclencher manuellement un workflow
 
```bash
curl -X POST http://localhost:5678/webhook/my-webhook-name \
  -H "Content-Type: application/json" \
  -d '{"key": "value"}'
```
 
### Monitorer l'exécution
 
- Allez à l'onglet **Executions** dans n8n
- Consultez les logs et les données d'entrée/sortie
- Vérifiez l'onglet **Evaluations** pour analyser les erreurs
### Publier un workflow
 
1. Cliquez sur le bouton **Publish** (en haut à droite)
2. Le workflow devient actif et réactif aux déclencheurs
3. Consultez le statut de publication et les statistiques
## 🏗️ Architecture
 
### Flux général
 
```
Déclencheur (Webhook/Chat/Formulaire)
    ↓
Filtre & Validation des données
    ↓
Extraction d'informations
    ↓
Logique conditionnelle (If/Else)
    ↓
Appel IA (Anthropic Chat Model)
    ↓
Traitement des résultats
    ↓
Stockage en base de données
    ↓
Notification/Réponse utilisateur
```
 
### Intégrations principales
 
| Intégration | Utilisation |
|-------------|-----------|
| Anthropic Chat | Traitement intelligent et réponses IA |
| Base de données | Stockage persistent des données |
| Webhooks | Déclenchement externe des workflows |
| APIs externes | Récupération et synchronisation des données |
 
## 📊 Exemples d'exécution
 
### Exemple 1 : Form Submission
```json
{
  "input": {
    "name": "Hamza",
    "email": "hamza@example.com",
    "message": "Je souhaite en savoir plus"
  },
  "output": {
    "status": "processed",
    "response": "Merci pour votre intérêt! Nous vous recontacterons bientôt.",
    "row_inserted": true
  }
}
```
 
### Exemple 2 : AI Chat
```json
{
  "input": {
    "sessionId": "39604...",
    "chatinput": "Quels sont vos horaires d'ouverture?",
    "action": "sendMessage"
  },
  "output": {
    "output": "Nous sommes ouverts de 9h à 18h du lundi au vendredi..."
  }
}
```
 
## 🔐 Sécurité
 
- ✅ Les clés API sont stockées dans les variables d'environnement
- ✅ Les webhooks doivent être protégés par authentification si nécessaire
- ✅ Utilisez HTTPS pour les connexions en production
- ✅ Limitez les permissions des comptes de base de données
- ✅ Activez les logs d'audit pour suivre les exécutions
## 🐛 Dépannage
 
### Le workflow ne se déclenche pas
- Vérifiez que le webhook est actif (bouton à côté du nœud)
- Consultez les logs dans **Executions > Failed**
- Assurez-vous que l'URL du webhook est correcte
### Erreurs de connexion à la base de données
- Vérifiez les paramètres de connexion (.env)
- Assurez-vous que la base de données est accessible
- Vérifiez les permissions de l'utilisateur DB
### Problèmes avec Anthropic API
- Vérifiez votre clé API et son quota
- Consultez le statut de l'API Anthropic
- Vérifiez les logs d'exécution pour le détail de l'erreur
## 📚 Documentation supplémentaire
 
- [Documentation n8n](https://docs.n8n.io/)
- [API Anthropic Claude](https://docs.anthropic.com/)
- [n8n Workflows Best Practices](https://docs.n8n.io/workflows/best-practices/)
## 🤝 Contribution
 
Les contributions sont bienvenues ! Pour contribuer :
 
1. **Fork** le repository
2. Créez une branche (`git checkout -b feature/AmazingFeature`)
3. Commitez vos changements (`git commit -m 'Add AmazingFeature'`)
4. Poussez vers la branche (`git push origin feature/AmazingFeature`)
5. Ouvrez une **Pull Request**
### Guidelines
- Documentez vos workflows dans ce README
- Exportez les workflows en JSON avant de pusher
- Testez complètement avant de soumettre une PR
- Suivez les conventions de nommage existantes
## 📈 Améliorations futures
 
- [ ] Ajouter des webhooks d'authentification
- [ ] Intégrer d'autres LLMs (OpenAI, Cohere)
- [ ] Ajouter des tests automatisés
- [ ] Créer un dashboard de monitoring
- [ ] Implémenter du rate limiting
- [ ] Ajouter la gestion des erreurs avancée
## 📞 Support
 
Pour les questions ou problèmes :
- Ouvrez une **[Issue](https://github.com/hamzaaithammou-tech/N8N-automation/issues)** sur GitHub
- Consultez les **[Discussions](https://github.com/hamzaaithammou-tech/N8N-automation/discussions)**
- Contactez-moi via email : hamza@example.com
## 📄 Licence
 
Ce projet est sous licence MIT. Voir le fichier [LICENSE](LICENSE) pour plus de détails.
 
## ⭐ Supportez ce projet
 
Si ce repository vous a été utile, n'hésitez pas à donner une ⭐ !
 
---
 
**Créé avec ❤️ par [Hamza Aithammou](https://github.com/hamzaaithammou-tech)**
 
*Dernière mise à jour : 2026*
