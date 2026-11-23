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

Champs facultatifs :
- `"open": "fichier-ouvert.glb"` : modèle déplié. Le clic joystick (ou le bouton « Lit ») échange alors le modèle fermé et le modèle ouvert, au lieu d'afficher l'encombrement bleu.
- `"anchor": "back"` : le modèle est déjà à l'échelle 1:1, avec son origine au sol, au milieu du dos. Il n'est ni recentré ni déformé : on vise le pied du mur et le dos s'y plaque.
- `"y": 1.45` : hauteur de pose en mètres (miroir, tableau). `"wall": true` : si on vise directement un mur, l'objet s'accroche à l'endroit visé.
- `"parts": [{"file": "a.glb", "open": "a-ouvert.glb"}, {"file": "b.glb", "y": 1.45}]` : ensemble de plusieurs fichiers posés d'un coup.
- `"default": true` : meuble choisi à l'ouverture de la page.

Le reflet du miroir et les reflets du cuir viennent de `meubles/env-salon.jpg` (panorama d'un salon ressemblant) : une page web n'a pas accès aux caméras du casque.

## Canapé de Cécile (23/11/2026)
- `canape-cuir.glb` et `canape-cuir-ouvert.glb` : canapé cuir anthracite 200 × 90 × 85 cm, assise à 45 cm ; déplié : couchage 140 × 190 cm, 212 cm depuis le mur.
- `miroir-laiton.glb` : miroir rond Ø 70 cm, cadre laiton, centre à 145 cm du sol (25 cm au-dessus du dossier).
- Sources Blender et scripts : dossier `canape-cecile` (hors dépôt).

## Commandes dans le Quest
- Gâchette : poser le meuble choisi
- Grip maintenu : attraper et déplacer le meuble le plus proche
- Joystick gauche/droite : tourner
- A / X : meuble suivant · B / Y : supprimer
- Clic joystick : déplier / replier le canapé convertible (ou encombrement du lit ouvert pour les autres meubles)
- Viser un mur plutôt que le sol : le meuble s'aligne dos au mur ; le miroir seul s'accroche à l'endroit visé
