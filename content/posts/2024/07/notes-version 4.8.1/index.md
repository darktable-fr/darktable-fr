---
title: "Version corrective 4.8.1"
aliases:
  - "darktable-4-8-1"
date: "2024-07-21"
featured: true
categories:
  - "actualites"
  - "featured"
tags:
  - "featured"
authors:
  - "jipivy"
coverImage: "images/dt_logo-4.8.1.png"
---

La version 4.8.1 de darktable est sortie xxx dernier.

Voici la traduction française des notes de version.

Merci à [Deepl](https://deepl.com/) pour l'aide précieuse.

<div align="right">Jean-Pierre Verrue</div>

___

Nous sommes fiers d'annoncer la nouvelle version de darktable, 4.8.1 !

La version github est disponible ici : [https://github.com/darktable-org/darktable/releases/tag/release-4.8.0](https://github.com/darktable-org/darktable/releases/tag/release-4.8.0).

Comme toujours, n'utilisez pas le fichier tarball autogénéré fourni par
github, mais uniquement notre fichier tar.xz. Les sommes de contrôle sont :

```
$ sha256sum darktable-4.8.1.tar.xz
???  darktable-4.8.1.tar.xz
$ sha256sum darktable-4.8.1-x86_64.dmg (macOS 13.5)
???  darktable-4.8.1-x86_64.dmg
$ sha256sum darktable-4.8.1-arm64.dmg (macOS 14.0)
???  darktable-4.8.1-arm64.dmg
$ sha256sum darktable-4.8.1-win64.exe
???  darktable-4.8.1-win64.exe
```

Lors de la mise à jour à partir de la série stable 4.6.x, gardez à l'esprit que
vos modifications seront préservées pendant ce processus, mais que la nouvelle
bibliothèque et la configuration ne seront plus utilisables avec la version 4.6.x.

#### Note importante :
Pour s’assurer que darktable supporte le format de fichier RAW de votre appareil
photo, veuillez lire [ce post](https://discuss.pixls.us/t/raw-samples-wanted/5420?u=lebedevri).
Vous y apprendrez comment contribuer à la constitution de l’ensemble d’échantillons
d’images (sous licence CC0) pour votre boîtier.


Depuis darktable 4.8.0 :

- 93 commits à darktable + rawspeed  
- 26 demandes de pull traitées  
- 1 problème fermé

## Les grandes nouveautés
- n/a

## Autres changements
- n/a

## Correction de bogues

Fixed export without high quality sampling but with up-scaling activated.
Fixed support for all vectorscope modes when using CMYK profiles as for softproofing.
Fixed empty lighttable when importing from command-line. Now darktable opens lighttable on first filmroll when importing from command-line.
Fixed color picker area resizing using corners when heavy distorting is applied into image.
Fixed wrong cropping in rotate and perspective module with strong rotation and automatic cropping set to "original format".
Fixed possible color shift (pink) when using the Retouch module with the embedded lens correction module.
Fixed histogram display when using a color picker area on a rotated or flipped image.
Fixed a crash while using the -d imageio option.
Fixed large image exports due to a bug in finalscale module.
Fixed failure to load valid JPEG2000 files with unspecified color space.
Fixed image jump if collection is empty.

## Lua

### API Version
- La version de l'API est maintenant la 9.3.0

### Correction de bogues
n/a

### Add action support for Lua
n/a

### Autres changements Lua
n/a

## Notes


- Exporting with up-scaling and whithout using the high quality option will result in corrupt images.

- Lors de l'exportation vers les formats AVIF, EXR, JPEG XL ou XCF, la
  sélection de métadonnées spécifiques (par exemple, géomarquage ou
  créateur) n'est actuellement pas possible. Pour les formats AVIF,
  EXR, JPEG XL et XCF, darktable n'inclura aucun champ de métadonnées
  à moins que l'utilisateur ne sélectionne toutes les cases à cocher
  dans les options de Préférence du module d'exportation.

- In order to support the correct display of numbers in darktable, the minimum supported Gtk version has had to be increased to 3.24.15. For people who need to build darktable with an older version, this can be achieved by removing line 241 of the darktable.css file on your system. See https://github.com/darktable-org/darktable/issues/13166.
  
-  La version 4.8 ne prend plus en charge les versions de macOS antérieures
  à 13.5.

## Changement de dépendances

### Obligatoires

- La version minimale de libpng 1.5.x est désormais requise.
- La version 0.27.2 d'Exiv2 est désormais requise.
- La version minimale de pugixml 1.5 est désormais requise.
- La version minimale de libcurl 7,56 est désormais requise.

### Optionnelle(s)

- n/a

## Changements RawSpeed

- Les appareils Fujifilm équipés du capteur X-Trans 4 et les appareils
  plus récents utilisent désormais le recadrage fourni par le boîtier.

## Supports d'appareils, comparés à la version 4.6

### Support de base

Canon EOS R100 (requires LibRaw 202403 and later)
Canon EOS R50 (requires LibRaw 202403 and later)
Canon EOS R6 Mark II (requires LibRaw 202403 and later)
Canon EOS R8 (requires LibRaw 202403 and later)
Canon EOS Ra (requires LibRaw 202403 and later)
Fujifilm FinePix S9600fd
Fujifilm X100VI (compressed)
GoPro FUSION (DNG)
Leica SL3 (DNG)
OM System OM-1 Mark II
Panasonic DC-TZ95D (4:3)
Panasonic DMC-FX150 (4:3, 3:2, 16:9)
Panasonic DMC-FZ28 (3:2)
Phase One P25+
Phase One P45+
Ricoh GR III HDF (DNG)
Ricoh GR IIIx HDF (DNG)
Sony ILCE-9M3
Sony UMC-R10C

### Préréglages de la balance des blancs

Canon EOS R6 Mark II (requires LibRaw 202403 and later)
Fujifilm X-H2
OM System OM-1 Mark II
OM System OM-5

### Profils de bruit

Canon EOS R6 Mark II (requires LibRaw 202403 and later)
Fujifilm GFX 50R
OM System OM-1 Mark II
OM System OM-5
Phase One IQ180
Sony ILCE-9M3
Sony ZV-1

### Absence de prise en charge du mode de compression

Apple ProRAW DNGs
CinemaDNG lossless (Blackmagic, some DJI, etc.) and lossy (Blackmagic)
DNG 1.7 using JPEG XL (Adobe enhanced, Samsung Expert RAW)
Fujifilm lossy RAFs
Nikon high efficiency NEFs
OM System 14-bit high resolution ORFs
Sony downsized lossless ARWs ("M" for full-frame, "S" for full-frame & APS-C)

### Fin de support

La prise en charge des appareils suivants est suspendue car aucun
échantillon n'est disponible sur raw.pixls.us :

Creo/Leaf Aptus 22(LF3779)/Hasselblad H1
Fujifilm IS-1
Kodak EasyShare Z980
Leaf Aptus-II 5(LI300059)/Mamiya 645 AFD
Leaf Credo 60
Leaf Credo 80
Minolta DiMAGE 5
Olympus SP320
Phase One IQ250
Sinar Hy6/ Sinarback eXact
ST Micro STV680

## Traductions

Czech
German
European Spanish
Finnish
French
Hungarian
Italian
Japanese
Dutch
Polish
Brazilian Portuguese
Russian
Slovenian
Albanian
Ukrainian
Chinese (Simplified)
Chinese (Traditional)