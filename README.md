# ACCÈS+ — Tableau de bord du comité de pilotage

Application web installable (PWA) reproduisant le tableau de bord de suivi
physique et financier de la composante C2 du programme ACCÈS+ (AGEFAU).

**Important — stockage des données** : les données saisies (avancement,
budget, PV/EV/AC, fréquentation des CAU) sont enregistrées uniquement dans
le navigateur de l'appareil utilisé (téléphone ou ordinateur), via
`localStorage`. Il n'y a **aucune synchronisation** entre le téléphone et
le web : ce que vous saisissez sur votre téléphone n'apparaît pas sur
l'ordinateur, et inversement. C'est le fonctionnement le plus simple et
gratuit ; si vous avez besoin de données partagées entre plusieurs
appareils ou plusieurs personnes, il faudra ajouter un service de stockage
externe (ex. Firebase, Google Sheets) — ce n'est pas inclus ici.

---

## 1. Mettre le projet en ligne avec GitHub Pages

Aucune ligne de commande n'est nécessaire — tout se fait depuis le site
github.com.

1. Connectez-vous sur [github.com](https://github.com) (créez un compte
   gratuit si besoin).
2. Cliquez sur le bouton **+** en haut à droite → **New repository**.
   - Nom du dépôt : par exemple `acces-plus-dashboard`.
   - Visibilité : **Public** (nécessaire pour que GitHub Pages héberge le
     site gratuitement).
   - Ne cochez pas « Add a README file » (vous en déposez déjà un).
   - Cliquez sur **Create repository**.
3. Sur la page du dépôt vide, cliquez sur **uploading an existing file**
   (ou **Add file → Upload files**).
4. Glissez-déposez **tous les fichiers et dossiers** fournis en conservant
   la structure :
   ```
   index.html
   manifest.json
   sw.js
   icons/icon-192.png
   icons/icon-512.png
   icons/icon-maskable-512.png
   ```
   (GitHub accepte le glisser-déposer d'un dossier complet depuis
   l'explorateur de fichiers de votre ordinateur.)
5. En bas de page, cliquez sur **Commit changes**.
6. Allez dans l'onglet **Settings** du dépôt → menu **Pages** (dans la
   colonne de gauche).
7. Sous **Build and deployment → Source**, choisissez **Deploy from a
   branch**. Sous **Branch**, choisissez **main** et le dossier **/ (root)**,
   puis **Save**.
8. Patientez environ une minute, puis rechargez la page **Settings → Pages** :
   l'URL de votre site apparaît en haut, du type :
   ```
   https://VOTRE-NOM-UTILISATEUR.github.io/acces-plus-dashboard/
   ```
   C'est l'adresse de votre tableau de bord, accessible depuis n'importe
   quel navigateur (ordinateur ou téléphone).

---

## 2. Installer l'application sur Android

1. Ouvrez l'URL ci-dessus dans **Chrome** sur votre téléphone Android.
2. Un bouton **« Installer l'application »** apparaît dans l'en-tête du
   tableau de bord — appuyez dessus. (S'il n'apparaît pas immédiatement,
   ouvrez le menu ⋮ de Chrome en haut à droite → **Ajouter à l'écran
   d'accueil** / **Installer l'application**.)
3. Une icône « A+ » apparaît sur votre écran d'accueil. En l'ouvrant,
   l'application se lance en plein écran, comme une application native.
4. L'application fonctionne aussi hors connexion après une première
   ouverture (le contenu est mis en cache automatiquement).

## 3. Utilisation sur ordinateur (web)

Ouvrez simplement la même URL dans un navigateur de bureau (Chrome, Edge,
Firefox). Dans Chrome ou Edge, une icône d'installation apparaît aussi
dans la barre d'adresse pour installer le tableau de bord comme
application de bureau.

---

## 4. Mettre à jour le tableau de bord plus tard

Pour modifier le contenu (nouvelles cibles, nouveaux jalons, etc.) :
remplacez le fichier `index.html` par une nouvelle version dans le dépôt
GitHub (**Add file → Upload files**, en écrasant l'ancien fichier), puis
**Commit changes**. GitHub Pages republie automatiquement le site en
quelques dizaines de secondes.

Si vous changez le contenu de fond de l'application, incrémentez le
numéro de version dans `sw.js` (ligne `CACHE_NAME = "acces-plus-dashboard-v1"`
→ `v2`, etc.) pour forcer les appareils à récupérer la nouvelle version
plutôt que l'ancienne mise en cache.
