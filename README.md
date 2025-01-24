# README : Script de Configuration de l'Environnement de Développement

## Description

Ce script Bash **automatisé** permet d'installer les langages de programmation et leurs frameworks associés sur **Linux**, **macOS** et **Windows** (via un environnement compatible comme Git Bash). Il détecte le système d'exploitation et exécute les commandes adaptées.

Il inclut la vérification préalable de chaque langage et framework, et propose à l'utilisateur d'installer uniquement ce qui n'est pas déjà présent.

---

## Fonctionnalités

1. **Détection automatique du système d'exploitation :**
   - Linux (via `apt`).
   - macOS (via `Homebrew`).
   - Windows (via `winget` exécuté dans Git Bash ou un environnement compatible Bash).

2. **Langages supportés :**
   - Python
   - Ruby
   - Node.js
   - PHP
   - Go
   - Java (OpenJDK)
   - Rust

3. **Frameworks supportés :**
   - Django (Python)
   - Flask (Python)
   - Rails (Ruby)
   - Express (Node.js)
   - Laravel (PHP)
   - Gin (Go)
   - Spring Boot CLI (Java)
   - Rocket (Rust)

4. **Exécution des commandes spécifiques aux OS :**
   - Les commandes Homebrew s'exécutent sous l'utilisateur non-root même si le script est lancé avec `sudo`.
   - Les installations via `pip3` utilisent l'option `--user` pour éviter les conflits de permissions.

5. **Installation interactive :**
   - L'utilisateur est invité à confirmer ou refuser chaque installation.

---

## Prérequis

### Linux
- Le script nécessite `apt` comme gestionnaire de paquets (Ubuntu, Debian ou dérivés).

### macOS
- Homebrew doit être installé. Si ce n'est pas le cas, le script propose une installation automatique.

### Windows
- Utilisez **Git Bash** ou un terminal compatible Bash.
- Assurez-vous que **winget** (Windows Package Manager) est installé et configuré.

---

## Installation et Utilisation

### 1. Téléchargez le script

Copiez ou téléchargez le fichier `setup_dev_env.sh` dans le répertoire de votre choix. Assurez-vous qu'il est lisible et exécutable.

### 2. Rendez le script exécutable

Avant de lancer le script, vous devez lui attribuer les permissions d'exécution :

```bash
chmod +x ./setup_dev_env.sh
```

### 3. Exécutez le script

Lancez le script en fonction de votre système d'exploitation :

#### Sur Linux ou macOS
Exécutez simplement la commande suivante (avec `sudo` si nécessaire) :

```bash
sudo ./setup_dev_env.sh
```

#### Sur Windows
1. Ouvrez **Git Bash** ou un terminal compatible Bash.
2. Exécutez le script avec la commande :

```bash
bash ./setup_dev_env.sh
```

---

## Détails d'Installation

### Vérifications des Langages
Pour chaque langage, le script :
1. Vérifie si le langage est déjà installé.
2. Si le langage n'est pas trouvé, il propose à l'utilisateur de l'installer.
3. Adapte les commandes en fonction du système d'exploitation.

### Vérifications des Frameworks
Pour chaque framework, le script :
1. Vérifie s'il est déjà installé (par exemple, via `pip3 show` pour Django ou `gem list` pour Rails).
2. Si le framework n'est pas trouvé, il propose à l'utilisateur de l'installer.

---

## Contenu Supporté

### Langages
| Langage    | Vérification         | Installation Mac               | Installation Linux             | Installation Windows                     |
|------------|----------------------|--------------------------------|--------------------------------|------------------------------------------|
| Python     | `python3`            | `brew install python`          | `apt install -y python3`       | `winget install --id Python.Python.3`    |
| Ruby       | `ruby`               | `brew install ruby`            | `apt install -y ruby-full`     | `winget install --id RubyInstallerTeam.RubyWithDevKit` |
| Node.js    | `node`               | `brew install node`            | `curl -fsSL https://deb.nodesource.com/setup_18.x | bash - && apt install -y nodejs` | `winget install --id OpenJS.NodeJS.LTS` |
| PHP        | `php`                | `brew install php composer`    | `apt install -y php-cli composer` | `winget install --id PHP.PHP`          |
| Go         | `go`                 | `brew install go`              | `apt install -y golang`        | `winget install --id Golang.Go`         |
| Java       | `java`               | `brew install openjdk@17`      | `apt install -y openjdk-17-jdk` | `winget install --id EclipseAdoptium.OpenJDK.17` |
| Rust       | `rustc`              | `curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh -s -- -y` | Même commande que Mac | `winget install --id Rustlang.Rust` |

### Frameworks
| Framework   | Langage   | Vérification                | Commande d'Installation                    |
|-------------|-----------|----------------------------|--------------------------------------------|
| Django      | Python    | `pip3 show django`         | `pip3 install --user django`               |
| Flask       | Python    | `pip3 show flask`          | `pip3 install --user flask`                |
| Rails       | Ruby      | `gem list -i rails`        | `gem install rails`                        |
| Express     | Node.js   | `npm list -g express`      | `npm install -g express-generator`         |
| Laravel     | PHP       | `composer global show laravel/installer` | `composer global require laravel/installer` |
| Gin         | Go        | `go list -m github.com/gin-gonic/gin` | `go install github.com/gin-gonic/gin@latest` |
| Spring Boot | Java      | `command -v spring`        | `curl -fsSL https://start.spring.io | bash` |
| Rocket      | Rust      | `cargo install --list | grep rocket` | `cargo install rocket`                    |

