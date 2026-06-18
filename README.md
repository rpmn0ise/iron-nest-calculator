# 🎯 Iron Nest - Balistic Calculator

[Français](#-version-française) | [English](#-english-version)

---

## 🇫🇷 Version Française

### ❓ Pourquoi ce calculateur externe ? (Philosophie du Projet)
La question revient souvent sur Discord : *« Pourquoi créer un outil externe alors qu’un calculateur balistique performant existe déjà directement intégré en jeu ? »*

1. **La Vitesse vs L'Immersion :** Le calculateur intégré au jeu est une excellente réussite en termes de réalisme et d'immersion (tourner des roues graphiques, ajuster finement des curseurs à la souris, etc.). Cependant, en conditions de combat de haute intensité, ce processus mécanique est fastidieux, rigide et chronophage.
2. **Confort Multi-Écran :** Cet outil a été pensé pour s'intégrer sur un **deuxième écran**. Pendant que votre écran principal affiche l'action, le calculateur externe attend vos saisies au clavier. Pas de menus superflus, pas d'animations.
3. **Efficacité Brute :** Saisie instantanée de la distance et de l'azimut au pavé numérique $\rightarrow$ Affichage immédiat des degrés d'élévation requis. Vous gagnez de précieuses secondes cruciales pour corriger un tir ou devancer une contre-batterie ennemie.

### ⚙️ Comment ça fonctionne ? (La Logique Mathématique)
Le calculateur en jeu utilise une table de tir segmentée en **6 paliers de charges (P.C.)**, chacun couvrant une tranche de 5 kilomètres. Le jeu applique une méthode d'**interpolation linéaire dynamique** au sein de bornes de base.

1. **Sélection du palier :** Détermination automatique des charges propulsives requises (`P.C. = Math.ceil(distance / 5)`).
2. **Recherche de la borne inférieure (Base Key) :** Identification de la borne kilométrique officielle enregistrée immédiatement *inférieure* à la position de la cible.
3. **Calcul de l'écart (Delta) :** Extraction de l'écart par tranches de 10 mètres (0.01 km).
4. **Interpolation au coefficient :** Le delta de pas de 10m est multiplié par le coefficient spécifique du palier puis ajouté à l'élévation de base.

> **Exemple pour 5.33 km :** Borne de base à 5.1 km (30.60°) + (23 tranches de 10m $\times$ coefficient 0.06°) = **31.98°**. Concordance parfaite au centième de degré près avec le jeu !

### 🚀 Fonctionnalités majeures
* **Zéro clic requis :** Calcul dynamique et instantané à chaque touche pressée (`oninput`).
* **Précision millimétrée :** Algorithme synchronisé sur les données réelles du jeu.
* **Interface double mode :** *Mode Bunker* (Sombre) haute visibilité pour la nuit et *Mode État-Major* (Clair) style carte rétro.
* **Internationalisation (i18n) :** Support natif et bascule instantanée entre le Français (FR) et l'Anglais (EN).
* **Ultra-léger :** Un seul fichier autonome (`index.html`), sans aucune dépendance externe.

---

## 🇬🇧 English Version

### ❓ Why an external calculator? (Project Philosophy)
People on Discord often ask: *"Why build an external tool when a fully functional ballistic calculator already exists in-game?"*

1. **Speed vs. Immersion:** The in-game version is a masterpiece of immersion and realism (rotating graphical wheels, manual alignment, etc.). However, during high-intensity combat operations, this manual process becomes tedious, rigid, and time-consuming.
2. **Multi-Monitor Comfort:** This tool was explicitly designed to sit on a **second monitor**. While your main screen is focused on tactical gameplay, the external calculator waits for your keyboard inputs. No clutter, no animations.
3. **Raw Efficiency:** Type the distance and bearing on your numpad $\rightarrow$ immediately read the required gun elevation. You save precious seconds, allowing you to walk shots onto targets or outpace enemy counter-battery fire.

### ⚙️ How does it work? (Mathematical Logic)
The in-game calculator utilizes a firing table segmented into **6 powder charge steps (P.C.)**, each covering a 5-kilometer range bracket. The game relies on **dynamic linear interpolation** based on structured mileposts.

1. **Charge Selection:** Automatic determination of the required propellant (`P.C. = Math.ceil(distance / 5)`).
2. **Lower Bound Lookup (Base Key):** The tool identifies the closest registered milestone *below* the target's location.
3. **Delta Calculation:** It extracts the distance remainder in increments of 10 meters (0.01 km).
4. **Coefficient Interpolation:** The 10m step delta is multiplied by the specific bracket coefficient and then added to the baseline elevation.

> **Example for 5.33 km:** Base milestone 5.1 km (30.60°) + (23 steps of 10m $\times$ 0.06° coefficient) = **31.98°**. A flawless match down to the hundredth of a degree compared to the in-game UI!

### 🚀 Key Features
* **Zero Clicks Required:** Dynamic, instantaneous calculation executed on every keystroke (`oninput`).
* **Pinpoint Accuracy:** Tailored algorithm perfectly synchronized with actual game mechanics.
* **Dual Tactical Theme:** *Bunker Mode* (Dark) optimized for night ops (high-vis radar green/alert red) and *Staff Map Mode* (Light) with a retro paper finish.
* **Internationalization (i18n):** Native, single-click language toggle between French (FR) and English (EN).
* **Lightweight Architecture:** A single self-contained file (`index.html`) with zero external dependencies or heavy frameworks.

---

## 🛠️ Usage / Utilization

1. Open `index.html` in your web browser (and drag it to your secondary monitor).
2. Gather target **distance** (km) and **bearing / azimuth** (degrees) from your tactical map or spotters.
3. Input the data into the left panel.
4. Instantly read the firing data on the right panel (Powder charges, exact Gun Elevation, and Turret Azimuth).
5. Adjust your equipment in-game and open fire!

---
*Developed with precision for the artillery crews of Iron Nest. / Développé avec précision pour les artilleurs de l'Iron Nest.*
