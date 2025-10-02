# 🚀 System Manager Pro - Plugin aaPanel

[![Version](https://img.shields.io/badge/version-1.1.0-blue.svg)](https://github.com/pecorio-dev/aapanel-all-paid-for-free-plugins)
[![Python](https://img.shields.io/badge/python-3.6+-yellow.svg)](https://python.org)
[![aaPanel](https://img.shields.io/badge/aaPanel-compatible-orange.svg)](https://aapanel.com)

## 📋 Description

**System Manager Pro** est un plugin multi-fonctionnel pour aaPanel qui transforme votre serveur en une station de gestion complète. Il combine surveillance système, gestion des processus, contrôle des services et téléchargements avancés dans une interface web moderne et intuitive.

### ✨ Fonctionnalités principales

- 🖥️ **Gestionnaire de tâches** - Surveillance et contrôle des processus système
- ⚙️ **Gestionnaire de services** - Gestion complète des services systemctl
- 📥 **Gestionnaire de téléchargements** - Torrents, liens directs et YouTube
- 📊 **Monitoring en temps réel** - CPU, RAM, disque, réseau
- 📝 **Système de logs** - Traçabilité complète des actions
- 🔒 **Stockage sécurisé** - Protection des fichiers critiques
- 🌐 **Interface responsive** - Compatible mobile et desktop

## 🎯 Nouveautés v1.1.0

### 🔧 Améliorations techniques
- ✅ **transmission-rpc** - API Python native pour Transmission
- ✅ **Stockage local sécurisé** - Remplacement des bases de données
- ✅ **Gestion d'erreurs robuste** - Validation stricte des entrées
- ✅ **Cache intelligent** - Optimisation des performances
- ✅ **Scripts de diagnostic** - Résolution automatique des problèmes

### 🛠️ Corrections majeures
- ❌ **Suppression des bases de données** - 100% stockage local
- ❌ **Élimination des erreurs de résolution** - Scripts de réparation réseau
- ❌ **Protection des fichiers** - Système de fichiers protégés
- ❌ **Optimisation des performances** - Cache avec TTL

## 📦 Installation

### 🔍 Prérequis

- **Système** : Ubuntu 18.04+, Debian 10+, CentOS 8+
- **aaPanel** : Version 6.8.12 ou supérieure
- **Python** : 3.6 ou supérieur
- **Mémoire** : 512 MB RAM minimum
- **Disque** : 1 GB d'espace libre
- **Réseau** : Connexion internet pour les dépendances

### 🚀 Installation automatique (Recommandée)

```bash
# 1. Télécharger le plugin
cd /www/server/panel/plugin/
git clone https://github.com/aapanel/systemmanager.git

# 2. Exécuter l'installation corrigée
cd systemmanager
chmod +x install_fixed.sh
./install_fixed.sh
```

### 🔧 Installation avec diagnostic

Si vous rencontrez des problèmes de réseau :

```bash
# 1. Diagnostic des problèmes réseau
chmod +x diagnose_network.sh
./diagnose_network.sh

# 2. Réparation automatique
chmod +x fix_network_issues.sh
./fix_network_issues.sh

# 3. Test de connectivité
python3 test_connectivity.py

# 4. Installation
./install_fixed.sh
```

### 📋 Installation manuelle

```bash
# 1. Installer les dépendances système
apt update && apt install -y python3 python3-pip transmission-daemon aria2

# 2. Installer les dépendances Python
pip3 install psutil requests transmission-rpc yt-dlp aria2p

# 3. Configurer les permissions
chmod +x systemmanager_main.py
chmod 755 downloads torrents logs

# 4. Démarrer Transmission
systemctl enable transmission-daemon
systemctl start transmission-daemon
```

## 🎮 Utilisation

### 🌐 Interface Web

Accédez au plugin via **aaPanel > App Store > System Manager Pro**

#### 🏠 Dashboard
- Vue d'ensemble du système en temps réel
- Graphiques de performance (CPU, RAM, disque)
- Actions rapides et raccourcis
- Informations système détaillées

#### 🖥️ Gestionnaire de tâches
```bash
# Fonctionnalités disponibles
- Liste des processus avec tri et filtrage
- Informations détaillées (PID, CPU, RAM, utilisateur)
- Actions : Terminer (SIGTERM), Forcer (SIGKILL)
- Recherche en temps réel
- Protection des processus système
```

#### ⚙️ Gestionnaire de services
```bash
# Contrôles disponibles
- Start/Stop/Restart des services
- Enable/Disable au démarrage
- Statut détaillé avec logs
- Services de démarrage
- Protection des services critiques
```

#### 📥 Gestionnaire de téléchargements

##### 🧲 Torrents (transmission-rpc)
```python
# Ajout de torrents
- URL magnet : magnet:?xt=urn:btih:...
- Fichiers .torrent
- Contrôle complet (start/stop/remove)
- Statistiques détaillées
- Interface web Transmission sur port 9091
```

##### 🔗 Téléchargements directs (aria2c)
```bash
# Liens supportés
- HTTP/HTTPS
- FTP
- Téléchargements multi-connexions
- Reprise automatique
```

##### 🎥 YouTube et médias (yt-dlp)
```bash
# Plateformes supportées
- YouTube, Vimeo, Dailymotion
- Plus de 1000 sites
- Extraction audio/vidéo
- Qualité sélectionnable
```

### 🔧 API et intégration

#### Endpoints disponibles
```python
# Système
POST /systemmanager/get_system_stats
POST /systemmanager/get_storage_info

# Processus
POST /systemmanager/get_processes
POST /systemmanager/kill_process
POST /systemmanager/get_process_details

# Services
POST /systemmanager/get_services
POST /systemmanager/control_service
POST /systemmanager/get_service_status

# Téléchargements
POST /systemmanager/add_torrent
POST /systemmanager/get_torrents
POST /systemmanager/control_torrent
POST /systemmanager/download_link
POST /systemmanager/get_downloads

# Logs et utilitaires
POST /systemmanager/get_logs
POST /systemmanager/clear_logs
POST /systemmanager/cleanup_storage
```

#### Exemple d'utilisation
```python
import requests

# Récupérer les statistiques système
response = requests.post('http://your-server/systemmanager/get_system_stats')
stats = response.json()

# Ajouter un torrent
data = {'url': 'magnet:?xt=urn:btih:...'}
response = requests.post('http://your-server/systemmanager/add_torrent', json=data)
```

## 🔧 Configuration

### 📁 Structure des fichiers
```
/www/server/panel/plugin/systemmanager/
├── systemmanager_main.py      # Module principal
├── local_storage.py           # Gestionnaire de stockage
├── file_manager.py           # Gestionnaire de fichiers
├── config.json               # Configuration
├── info.json                 # Métadonnées du plugin
├── index.html                # Interface web
├── static/                   # Ressources statiques
│   ├── css/
│   ├── js/
│   └── images/
├── data/                     # Données du plugin
│   ├── protected/            # Fichiers protégés
│   ├── cache/               # Cache temporaire
│   └── user_files/          # Fichiers utilisateur
├── downloads/               # Téléchargements
├── torrents/               # Fichiers torrents
└── logs/                   # Logs du plugin
```

### ⚙️ Configuration avancée

#### Transmission
```json
{
  \"rpc_port\": 9091,
  \"download_dir\": \"/www/server/panel/plugin/systemmanager/downloads\",
  \"peer_port\": 51413,
  \"speed_limit_down\": 0,
  \"speed_limit_up\": 0
}
```

#### Cache et performance
```json
{
  \"cache_enabled\": true,
  \"cache_duration\": 300,
  \"max_memory_usage_mb\": 512,
  \"background_tasks\": true
}
```

#### Sécurité
```json
{
  \"allowed_kill_users\": [\"root\", \"www-data\"],
  \"forbidden_processes\": [\"init\", \"kernel\", \"systemd\"],
  \"max_file_size_mb\": 1024,
  \"scan_downloads\": true
}
```

## 🛠️ Dépannage

### 🔍 Problèmes courants

#### Erreurs de résolution DNS
```bash
# Diagnostic
./diagnose_network.sh

# Réparation automatique
./fix_network_issues.sh

# Configuration manuelle
echo 'nameserver 8.8.8.8' > /etc/resolv.conf
echo 'nameserver 1.1.1.1' >> /etc/resolv.conf
```

#### Problèmes de dépendances Python
```bash
# Utiliser des miroirs alternatifs
pip3 install -i https://mirrors.aliyun.com/pypi/simple/ transmission-rpc

# Mettre à jour pip
pip3 install --upgrade pip

# Installation sans SSL
pip3 install --trusted-host pypi.org transmission-rpc
```

#### Transmission non accessible
```bash
# Vérifier le service
systemctl status transmission-daemon

# Redémarrer
systemctl restart transmission-daemon

# Vérifier la configuration
cat /etc/transmission-daemon/settings.json

# Tester l'accès
curl http://localhost:9091/transmission/rpc
```

### 📋 Scripts de diagnostic

#### Test rapide
```bash
# Test de connectivité
python3 test_connectivity.py

# Diagnostic complet
./diagnose_network.sh

# Réparation automatique
./fix_network_issues.sh
```

#### Logs et débogage
```bash
# Logs du plugin
tail -f /www/server/panel/plugin/systemmanager/logs/systemmanager.log

# Logs système
journalctl -u transmission-daemon -f

# Test du plugin
python3 systemmanager_main.py
```

### 🆘 Support

Si les problèmes persistent :

1. **Générez un rapport de diagnostic**
   ```bash
   ./diagnose_network.sh > diagnostic_report.txt
   ```

2. **Collectez les informations système**
   ```bash
   uname -a > system_info.txt
   cat /etc/os-release >> system_info.txt
   ```


## 🔒 Sécurité

### 🛡️ Fonctionnalités de sécurité

- **Validation stricte** des entrées utilisateur
- **Protection des processus** système critiques
- **Fichiers protégés** avec codes de confirmation
- **Logs de sécurité** pour traçabilité
- **Limitation des permissions** par utilisateur
- **Scan automatique** des téléchargements

### 🔐 Bonnes pratiques

```bash
# Limiter l'accès Transmission
ufw allow from 127.0.0.1 to any port 9091

# Surveiller les logs
tail -f /www/server/panel/plugin/systemmanager/logs/security_log.json

# Sauvegarder régulièrement
./systemmanager/backup_data.sh
```

## 🚀 Performance

### 📊 Optimisations

- **Cache intelligent** avec TTL configurable
- **Requêtes asynchrones** pour l'interface
- **Pagination** des grandes listes
- **Compression** des données transmises
- **Limitation** des ressources système

### 📈 Métriques

```python
# Statistiques de performance
{
  \"cache_hit_ratio\": \"85%\",
  \"average_response_time\": \"120ms\",
  \"memory_usage\": \"45MB\",
  \"active_downloads\": 3,
  \"system_load\": \"0.8\"
}
```

## 🤝 Contribution

### 🛠️ Développement

```bash
# Cloner le repository
git clone https://github.com/aapanel/systemmanager.git

# Installer les dépendances de développement
pip3 install -r requirements-dev.txt

# Lancer les tests
python3 -m pytest tests/

# Vérifier le code
flake8 systemmanager/
```

### 📝 Guidelines

1. **Code style** : PEP 8
2. **Documentation** : Docstrings obligatoires
3. **Tests** : Couverture > 80%
4. **Sécurité** : Validation des entrées
5. **Performance** : Profiling requis

## 🙏 Remerciements

- **aaPanel Team** pour la plateforme
- **Transmission Project** pour le client BitTorrent
- **yt-dlp Team** pour le téléchargeur multimédia
- **Aria2 Project** pour le gestionnaire de téléchargements
- **Communauté Open Source** pour les contributions



<div align=\"center\">
  <strong>🚀 System Manager Pro - Transformez votre serveur en station de gestion complète ! 🚀</strong>
</div>
