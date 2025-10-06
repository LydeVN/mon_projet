# :compass: Installation de Symfony

Cette documentation détaille chaque étape nécessaire pour installer et configurer **Symfony** sur **Windows**, lorsque **XAMPP** est déjà installé.  
> :bulb: Si PHP n’est pas installé, télécharge-le au préalable sur le [Site officiel](https://www.windows.php.net/download/).

---

## 1. Vérifier l’installation de PHP

Ouvre un terminal (cmd ou PowerShell) et tape :

```bash
php -v
```

- :white_check_mark: Si une version de PHP s’affiche, passe à l’**étape 3**.  
- :x: Sinon, il faut ajouter PHP à la variable d’environnement **PATH**.

---

## 2. Ajouter PHP à la variable d’environnement PATH

1. Ouvre ton **Explorateur de fichiers**  
2. Va dans le dossier :
   ```
   C:\xampp\php
   ```
3. Copie le chemin complet (ex : `C:\xampp\php`)
4. Dans la barre de recherche Windows, tape :
   ```
   variables d’environnement
   ```
   puis ouvre **Modifier les variables d’environnement système**
5. Clique sur **Variables d’environnement…**
6. Dans **Variables système**, sélectionne **Path** → **Modifier**
7. Clique sur **Nouveau** → colle le chemin :
   ```
   C:\xampp\php
   ```
8. Clique sur **OK** partout pour valider
9. Redémarre ton terminal et vérifie :
   ```bash
   php -v
   ```

---

## 3. Installer Scoop *(optionnel mais recommandé)*

Scoop est un gestionnaire de paquets pratique pour Windows, qui simplifie l’installation d’outils en ligne de commande.

Ouvre **PowerShell en mode administrateur** (sans être admin ça fonctionne aussi parfois) et exécute :

```powershell
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
iwr -useb get.scoop.sh | iex
```

Puis vérifie l’installation :

```bash
scoop --version
```

---

## 4. Installer Composer

Composer est le **gestionnaire de dépendances PHP** utilisé par Symfony.  
Télécharge-le ici : :point_right: [Composer](https://getcomposer.org/download/)
:warning: Lancer l'installation via le  `Composer-Setup.exe` téléchargeable sur la page.

Pendant l’installation :
1. Indique le chemin de PHP :  
   ```
   C:\xampp\php\php.exe
   ```
2. Laisse les options par défaut et termine l’installation
3. Vérifie ensuite :
   ```bash
   composer -v
   ```

---

## 5. Installer le CLI de Symfony

Le **Symfony CLI** facilite la création et la gestion des projets.

Télécharge-le ici : :point_right: [Symphony](https://symfony.com/download)

Ou installe-le via Scoop :
```bash
scoop install symfony-cli
```

Vérifie ensuite :
```bash
symfony -v
```

---

## 6. Activer les extensions PHP nécessaires

Certaines extensions doivent être activées pour que Symfony fonctionne correctement.

1. Va dans le dossier d’installation de XAMPP :
   ```
   C:\xampp
   ```
2. Ouvre le fichier :
   ```
   C:\xampp\php\php.ini
   ```
3. Recherche ces lignes et **supprime le point-virgule (;)** au début pour les activer :
   ```
   ;extension=intl
   ;extension=pdo_mysql
   ;extension=mbstring
   ;extension=zip
   ```
   Deviennent :
   ```
   extension=intl
   extension=pdo_mysql
   extension=mbstring
   extension=zip
   ```
4. Sauvegarde

Vérifie ensuite :
```bash
php -m
```

Tu devrais voir apparaître : `intl`, `pdo_mysql`, `mbstring`, `zip`.

---

## 7. Créer ton premier projet Symfony

Place-toi dans ton dossier de développement :
```bash
cd C:\chemin\vers\ton_projet
```

Puis exécute :
```bash
symfony new mon_projet --webapp
```

Une fois créé, démarre le serveur interne :
```bash
cd mon_projet
symfony serve
```

---

## 8. Vérification finale

Teste la commande suivante dans ton projet :
```bash
php bin/console
```
Lancé le serveur local via l'ip donné dans l'encadré vert après avoir fait la commande `symfony serve`
:white_check_mark: Si la liste des commandes Symfony s’affiche et que tu vois la page de test de symfony, ton environnement est prêt à l’emploi !