# 🧭 Installation de Symfony avec XAMPP (Windows)

Cette documentation détaille chaque étape nécessaire pour installer et configurer **Symfony** sur **Windows**, lorsque **XAMPP** est déjà installé.  
> 💡 Si PHP n’est pas installé, télécharge-le au préalable sur le site officiel.

---

## 1. Vérifier l’installation de PHP

Ouvre un terminal (cmd ou PowerShell) et tape :

```bash
php -v
```

- ✅ Si une version de PHP s’affiche, passe à l’étape suivante.  
- ❌ Sinon, il faut ajouter PHP à la variable d’environnement **PATH**.

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

Ouvre **PowerShell en mode administrateur** et exécute :

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
Télécharge-le ici : 👉 [https://getcomposer.org/download/](https://getcomposer.org/download/)

Pendant l’installation :
1. Indique le chemin de PHP :  
   ```
   C:\xampp\php\php.exe
   ```
2. Laisse les options par défaut et termine l’installation
3. Vérifie ensuite :
   ```bash
   composer -V
   ```

---

## 5. Installer le CLI de Symfony

Le **Symfony CLI** facilite la création et la gestion des projets.

Télécharge-le ici : 👉 [https://symfony.com/download](https://symfony.com/download)

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
4. Sauvegarde et redémarre **Apache** depuis le panneau XAMPP.

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

✅ Si la liste des commandes Symfony s’affiche, ton environnement est prêt à l’emploi !

---

## 🎉 Résumé rapide

| Étape | Objectif |
|-------|-----------|
| 1 | Vérifier PHP |
| 2 | Ajouter PHP au PATH |
| 3 | (Optionnel) Installer Scoop |
| 4 | Installer Composer |
| 5 | Installer Symfony CLI |
| 6 | Activer les extensions PHP |
| 7 | Créer le projet Symfony |
| 8 | Vérifier le bon fonctionnement |

---

> 🧑‍💻 Tu peux désormais commencer ton développement Symfony directement dans ton dossier `C:\xampp\htdocs` ou celui de ton choix !
