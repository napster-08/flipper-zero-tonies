# Toniebox NFC Fichiers

Ce dépôt contient des fichiers .nfc à utiliser avec Flipper Zero. Placez-les dans votre le dossier nfc, puis les émuler.


Annuaire

## Directory

Nous avons un répertoire de Tonies dans ce repo pour chaque langue, etant francais seul le repertoire french sera completé les autres repertoire sont un pull de nortakales:

* [English Tonies](English/README.md)
* [French Tonies](French/README.md)
* [German Tonies](German/README.md)


##Écriture sur le tag

Utilise SLI-Writer : c'est une application Flipper dédiée à l'écriture de l'UID sur les tags ISO 15693 magic, à partir des .nfc. Il existe aussi une version APK Android si compiler le FAP t'ennuie.

    Installe le FAP dans apps/NFC.
    Ouvre-le, sélectionne le .nfcde la figurine.
    Pose le tag magic sur l'antenne, centre-le bien, et laisse l'écriture se dérouler jusqu'au bout (le FAP écrit en plusieurs passes : blocs, puis UID).
    Vérifie en relisant le tag : UID identique et 8/8 blocs identiques. Un tag à moitié écrit ne casse rien mais ne fonctionnera pas.

Ne pas utiliser csetuid d'un Proxmark, ni interrompre l'écriture. Ensuite, c'est la box elle-même qui réactivera le privacy mode : la figurine clonée est autonome.
Les tags

Uniquement des magic SLIX-L (UID modifiable) de rfidfriend.com, variante magic. Les SLIX-L à UID fixe et les tags « programmable » génériques ne donnent rien sur une box stock. Les magic de rfidfriend fonctionnent aussi sur Toniebox 2, alors que l'émulation au Flipper, elle, se coupe au bout de deux minutes sur TB2 — raison de plus pour passer par un tag physique.

Le contenu audio n'est pas sur le tag : il reste sur la carte SD ou dans le cloud. La box le retrouve grâce à l'UID et le télécharge si besoin, donc la figurine clonée fonctionne aussi en ligne, et pourra être utilisée sur n'importe quelle box du foyer.

## Impression 3D
Le plan de la base. Le principe est contre-intuitif : le tag ne va pas au centre. Il y a une plaque métallique au milieu de la surface de lecture de la box, c'est une zone morte, et c'est là que va l'aimant. Le tag se place décalé d'environ 10 mm de l'axe, et légèrement au-dessus du plan de l'aimant.

Le schéma ci-dessus donne les proportions (vue de dessus à gauche, coupe à droite). Les cotes exactes à respecter :
-------------------------------------------------------------------------------------|
Élément	                       |     Valeur                                          |
-------------------------------|-----------------------------------------------------|
Diamètre de base	           |   60 mm minimum (65 mm si tu veux de la marge)      |
-------------------------------|-----------------------------------------------------|
Épaisseur de la base	       |   6 mm                                              |
-------------------------------|-----------------------------------------------------|
Décalage du centre du tag par  |                                                     |
rapport à l'axe	               |   10 à 11 mm                                        |
-------------------------------|-----------------------------------------------------|
Logement du tag	               |  ⌀39 mm, profondeur 0,5 mm,                         |
                               |  tag affleurant ou 0,5 mm en saillie                |
-------------------------------|-----------------------------------------------------|
Matière sous le tag	           |  0,8 mm (jamais plus de 1,5 mm)                     |
-------------------------------|-----------------------------------------------------|
Poche de l'aimant	           |  ⌀10,3 mm × 3,2 mm de profondeur, à l'axe           |
-------------------------------|-----------------------------------------------------|
Aimant	                       |  disque néodyme 10 × 3 mm, N35 ou plus              |
-------------------------------|-----------------------------------------------------|

La poche de l'aimant est au-dessus du plan du tag, côté intérieur de la figurine. C'est ce qui permet au tag de passer au-dessus de l'aimant sans que celui-ci ne dérègle sa bobine. Si tu préfères garder le tag bien à plat, descends l'aimant de 2 à 3 mm dans l'épaisseur du socle.
Pourquoi ces valeurs

    Avec un tag de 38 mm décalé de 10 mm, le bord du tag arrive à 29 mm du centre : il faut donc une base d'au moins 60 mm de diamètre, sinon le tag dépasse. Si tu prends des tags de 25 mm (stocktheyard en vend), une base de 50 mm suffit, le tag reste entièrement dans le disque et le montage est bien plus tolérant.
    La paroi de 0,8 mm sous le tag est le compromis : assez solide pour ne pas se percer, assez fine pour que le champ passe. Au-delà de 1,5 mm la portée s'effondre.
    L'aimant sur l'axe assure le maintien sur la plaque, exactement comme les figurines d'origine. Pour une figurine lourde, ajoute un second aimant derrière l'axe, à environ 20 mm, mais ne le mets jamais à moins de 5 mm de la bobine du tag.

Impression et assemblage

    Imprime la base à plat sur le plateau, poche d'aimant vers le haut.
    Fais une pause à la couche qui ferme la poche, insère l'aimant (peu importe la polarité), puis reprends : il sera prisonnier. Sinon, colle-le à la cyanoacrylate après coup.
    Le logement du tag est en face inférieure : tu peux y coller le tag en fin d'impression, ou le glisser à plat si tu as prévu un couvercle. Un bout de ruban adhésif fin le protège de l'abrasion.
    Teste avant de coller définitivement. Pose la base sur la box, vérifie qu'elle déclenche bien à plusieurs endroits de la surface et pas seulement sur un point précis. Si ça ne déclenche qu'à un seul endroit, le tag est trop profond ou trop centré.
    Oriente le décalage vers l'arrière de la figurine, pour que le visage soit tourné vers l'extérieur et que le montage reste reproductible.

À éviter

Pas de métal dans le corps de la figurine (vis, fil, peinture métallisée épaisse), base parfaitement plane, et pas de deuxième tag empilé sur le premier. Une figurine lourde ou haute bascule : garde le centre de gravité bas et la base large.

Deux modèles existent déjà tout faits si tu ne veux pas modéliser : « Traveltonie » et « NFC case with magnet - Tonie Base » (version paramétrable), tous deux sur MakerWorld, prévus pour des aimants 10 × 3 mm et des tags SLIX-L.
