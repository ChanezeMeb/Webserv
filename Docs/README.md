# Webserv

> Un serveur HTTP minimaliste écrit en C++98 pour l'école 42

## 📖 À propos

Webserv est un projet de l'école 42 consistant à créer un serveur web HTTP fonctionnel capable de gérer les requêtes des clients, de servir du contenu statique, et de traiter des scripts CGI. Ce projet approfondit votre compréhension des protocoles réseau, de la programmation système, et du traitement événementiel. Il vous apprend à implémenter les concepts fondamentaux des serveurs web modernes tels que nginx ou Apache : multiplexage I/O, configuration flexible, gestion des connexions multiples, et respect des standards HTTP/1.1.

### État du projet

Validé avec bonus. Grade : **125%** ✅⭐⭐

## 🎯 Fonctionnalités implémentées

### Protocole HTTP

- **Méthodes supportées** : GET, POST, DELETE (et HEAD optionnel)
- **HTTP/1.1 compliant** : Respect des standards HTTP avec codes de statut appropriés
- **Status codes** : 200 OK, 201 Created, 204 No Content, 301/302 Redirects, 400 Bad Request, 403 Forbidden, 404 Not Found, 405 Method Not Allowed, 413 Payload Too Large, 500 Internal Server Error, 501 Not Implemented, etc.
- **Headers HTTP** : Content-Type, Content-Length, Connection, Server, Location, etc.

### Configuration serveur

- **Format de configuration** : Style nginx pour une configuration intuitive
- **Paramètres globaux** : 
  - Timeout de connexion
  - Nombre maximum de clients simultanés
  - Taille maximale du body des requêtes
  - Nombre maximum d'événements poll
  - Backlog de connexions
- **Paramètres serveur** : 
  - Ports d'écoute configurables
  - Hosts/domaines multiples
  - Document root personnalisé
  - Pages d'erreur custom
- **Paramètres location** : 
  - Méthodes HTTP autorisées par route
  - Autoindex (listing de répertoires)
  - Index par défaut (index.html, index.htm, etc.)
  - Redirects internes
  - Alias de répertoires

### Serveur statique

- **Serveur de fichiers** : Capable de servir HTML, CSS, JavaScript, images, et autres assets statiques
- **Détection MIME** : Mapping automatique des extensions de fichier vers les types MIME
- **Gestion d'erreurs** : Pages d'erreur personnalisées pour chaque code HTTP
- **Directory listing** : Affichage optionnel du contenu des répertoires avec autoindex

### Traitement CGI

- **Support CGI** : Exécution de scripts serveur-side en Python, Perl, PHP
- **Upload de fichiers** : Traitement des requêtes POST avec body pour file uploads
- **Passage d'arguments** : Variables d'environnement CGI (SCRIPT_NAME, REQUEST_METHOD, QUERY_STRING, etc.)
- **Timeout CGI** : Gestion des scripts qui prennent trop de temps

### I/O Multiplexing

- **poll()** : Gestion efficace des connexions multiples sans threads
- **Alternativement** : Support de select(), epoll() (Linux), kqueue() (BSD/macOS)
- **Non-blocking sockets** : Sockets configurés en mode non-bloquant pour une architecture event-driven
- **Gestion des signaux** : Shutdown gracieux avec gestion de SIGTERM, SIGINT

### Gestion avancée

- **Connexions persistantes** : Keep-Alive optionnel pour réutilisation de connexions
- **Gestion des clients** : Limite configurable du nombre de clients simultanés
- **Timeouts** : Gestion des connexions inactives avec fermeture automatique
- **Logging** : Logs des requêtes et erreurs serveur
- **Sécurité basique** : Validation des requêtes, prévention du path traversal

## 🚀 Installation et compilation

### Prérequis

- Compilateur C++
- Make
- Système Unix/Linux (Linux, macOS, WSL)

### Installation optionnelle des interpréteurs CGI
