# Salon AR

Essayage de meubles à l'échelle 1:1 : aperçu 3D sur PC, réalité augmentée sur Meta Quest 3 (ou Chrome Android).

## Mise en ligne (GitHub Pages, gratuit)
1. Sur github.com, crée un dépôt public `salon-ar`.
2. « Add file » → « Upload files » : glisse `index.html` et le dossier `meubles/`.
3. Settings → Pages → Source : « Deploy from a branch », branche `main`, dossier `/ (root)` → Save.
4. Après 1 à 2 minutes, l'adresse est `https://<ton-pseudo>.github.io/salon-ar/`.
5. Dans le Quest : ouvre-la dans le navigateur, mets-la en favori, puis « Entrer en réalité augmentée ».

L'AR exige du HTTPS : un simple fichier ouvert depuis le disque ne marche pas.

## Ajouter des meubles
- Depuis l'appli : « Importer un GLB » (marche aussi dans le casque, avec un GLB téléchargé dans le Quest). Saisis ensuite les vraies cotes : le modèle est redimensionné.
- Ou dans le dépôt : dépose le fichier dans `meubles/` et ajoute une ligne dans `meubles/meubles.json` :

```json
[
  {"name": "Canapé cuir Sketchfab", "file": "canape.glb", "L": 2.10, "P": 0.95, "H": 0.85, "bed": 2.05}
]
```
Cotes en mètres ; `bed` = longueur une fois déplié (0 si non convertible).

## Commandes dans le Quest
- Gâchette : poser le meuble choisi
- Grip maintenu : attraper et déplacer le meuble le plus proche
- Joystick gauche/droite : tourner
- A / X : meuble suivant · B / Y : supprimer
- Clic joystick : encombrement du lit ouvert
