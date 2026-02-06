---
title: "Version 5.4.1"
aliases:
  - "darktable-5-4-1"
date: "2026-02-06"
featured: true
categories:
  - "actualites"
  - "featured"
tags:
  - "featured"
authors:
  - "jipivy"
coverImage: "images/dt_logo-5.4.1.png"
---

La version 5.4.1 de darktable est sortie ce vendredi.

Voici la traduction française des notes de version.

Merci à [Deepl](https://deepl.com/) pour l'aide précieuse.

Les binaires pour macOS, windows et appimage, sont disponibles en bas
de [cette page Github](https://github.com/darktable-org/darktable/releases/tag/release-5.4.1)
Ils seront également disponibles sur la page [install du site dartable.org](https://www.darktable.org/install/) dans quelques jours.
Les versions compilées spécifiquement pour les différentes distributions Linux seront disponibles
selon la diligence de leurs packageurs. En attendant, vous pouvez utiliser en toute sécurité,
la version [appimage](https://github.com/darktable-org/darktable/releases/download/release-5.4.1/Darktable-5.4.1-x86_64.AppImage).

<div align="right">Jean-Pierre Verrue</div>

___

Nous sommes fiers d'annoncer la nouvelle version de darktable, 5.4.1 !

La version github est disponible ici :
[https://github.com/darktable-org/darktable/releases/tag/release-5.2.1](https://github.com/darktable-org/darktable/releases/tag/release-5.4.1).

Comme toujours, n'utilisez pas le fichier tarball autogénéré fourni par
github, mais uniquement notre fichier tar.xz. Si vous ne construisez que pour vous-même
sans créer de paquetage pour une distribution quelconque, le clonage du code source
dans git est un moyen encore plus pratique.

Les sommes de contrôle sont :

```
$ sha256sum darktable-5.4.1.tar.xz
???  darktable-5.4.1.tar.xz

$ sha256sum darktable-5.4.1-arm64.dmg
???  darktable-5.4.1-arm64.dmg

$ sha256sum darktable-5.4.1-x86_64.dmg
???  darktable-5.4.1-x86_64.dmg

$ sha256sum darktable-5.4.1-win64.exe
???  darktable-5.4.1-win64.exe

$ sha256sum Darktable-5.4.1-x86_64.AppImage
???  Darktable-5.4.1-x86_64.AppImage
```

Lors de la mise à jour à partir de la série stable 5.2.x, gardez à l'esprit que
vos modifications seront préservées pendant ce processus, mais que la nouvelle
bibliothèque et la configuration ne seront plus utilisables avec la version 5.4.1


Il est fortement conseillé d'effectuer d'abord une sauvegarde.


#### Note importante :
Pour s’assurer que darktable supporte le format de fichier RAW de votre appareil
photo, veuillez lire [ce post](https://discuss.pixls.us/t/raw-samples-wanted/5420?u=lebedevri).
Vous y apprendrez comment contribuer à la constitution de l’ensemble complet d’échantillons
d’images (sous licence CC0) pour votre boîtier.

Depuis darktable 5.4.0 :

- 124 _commits_ vers darktable+rawspeed
-  74 _pull requests_ traitées
-  25 _issues_ fermées
  
_Veuillez noter que la documentation de darktable n'est pas encore complète pour la version 5.4
et que toutes les contributions sont très appréciées. Veuillez consulter la
[documentation du projet](https://github.com/darktable-org/dtdocs#contributing)
pour plus d'informations sur la manière de contribuer._

## Les grandes nouveautés

Voici un résumé des principales fonctionnalités ajoutées à darktable
5.4.1. Veuillez consulter le manuel de l'utilisateur pour plus de détails
sur les changements individuels (le cas échéant).

- N/A

## Améliorations de l'interface utilisateur (UI) et de l'expérience utilisateur (UX)

- N/A

## Améliorations des performances

- N/A

## Autres changements

- N/A

## Correction de bogues

- Fixed wrong handling of scaling factor during multi-preset export.

- Fixed missing help URL, pointing to the online documentation, for
  the new AgX module.

- Fixed wrong handling of overwrite if changed in export.

- Fixed images exported with wrong settings when using multi-preset
  export.

- Fixed wrong RAW specific auto-applied preset being applied to non
  RAW images.

- Fixed subtle color casts in bayer dual demosaicers.

- RustiCL gets the default optimizing compiler flags as other
  platforms.

- Fixed loading some Olympus ORF files (e.g. E-410 and E-510)
  due to a possible crash or memory corruption when parsing
  highlight-preservation Exif tag.

- Fixed the mask support in scale pixels module.

- Fixed a possible crash when using workspace due to the non
  deterministic ordering of the list of workspace read on disk.

- The list of the allowed tags in the metadata editor preferences has
  been restricted to tags which are supposed to be user-editable.

- Fixed the thumbnail information update in the overlay or the tooltip
  when some metadata variable are used. That is, when changing the
  metadata we need to recompute the thumbnail information.

- Fixed a possibly standstill while discarding history on fast
  systems.

- Fixed a possible crash in the way the Color Equalizer module GUI is
  initialized.

- Fixed an issue in culling layout where switching to the darkroom
  sometimes failed with an error message.

- Fixed an inconsistency in the styles module UI when shown in the
  darkroom view. It is not possible to create a duplicate to which the
  style is applied, and the setting of the corresponding checkbox has
  just been ignored. To avoid confusion, the checkbox is now hidden in
  the darkroom view.

- Fixes resets to default OpenCL per device setting.

- Fixed possibly outdated metadata when returning from darkroom. For
  example if the image is cropped in darkroom, the metadata $(WIDTH.x)
  and $(HEIGHT.x) where not correct on lighttable.

- Fixed a missing thumbnail overlays with $(CATEGORY[n,m]) variables
  update when a tag is assigned.

- Fixed jumping of curvature slider when used on the mask manager.

- Fixed a crash when mounting a camera from Darktable due to the
  current locale. Mounting is now done using the C locale.

## Lua

### API Version

- API version is now 9.6.0

### New Features

- N/A

### Bug Fixes

- N/A

### Add action support for Lua

### Other Lua changes

- N/A

## Notes

- When exporting to AVIF, EXR, JPEG XL, or XCF, selecting specific
  metadata (e.g. geo-tag or creator) is not currently possible. For
  AVIF, EXR, JPEG XL, and XCF formats, darktable will not include any
  metadata fields unless the user selects all of the checkboxes in the
  export module's preference options.

- Starting with release 5.4, macOS versions older than 14.0 are no
  longer supported on Apple Silicon Macs, nor older than macOS 15 on
  Intel Macs.

## Changed Dependencies

### Mandatory

- N/A

### Optional

- N/A

## RawSpeed changes

- N/A

## Camera support, compared to 5.4.0

### Base Support

- N/A

### White Balance Presets

- N/A

### Noise Profiles

- Canon EOS 10D
- Sony ILCE-7CR

### Missing Compression Mode Support

- Apple ProRAW DNGs
- CinemaDNG lossless (Blackmagic, some DJI, etc.) and lossy (Blackmagic)
- DNG 1.7 using JPEG XL (Adobe enhanced, Samsung Expert RAW)
- Fujifilm lossy RAFs
- Nikon high efficiency NEFs
- Phase One other than IIQ L
- Sony ARW 4.0/5.0 downsized lossless ("M" for full-frame, "S" for full-frame & APS-C) and ARW 6.0 lossy

### Suspended Support

Support for the following cameras is suspended because no samples are available on https://raw.pixls.us:

- Creo/Leaf Aptus 22(LF3779)/Hasselblad H1
- Fujifilm IS-1
- Kodak EasyShare Z980
- Leaf Aptus-II 5(LI300059)/Mamiya 645 AFD
- Leaf Credo 60
- Leaf Credo 80
- Olympus SP320
- Phase One IQ250
- ST Micro STV680

## Translations

- Czech
- German
- European Spanish
- Finnish
- French
- Hungarian
- Italian
- Japanese
- Korean
- Dutch
- Polish
- Brazilian Portuguese
- Slovenian
- Albanian
- Swedish
- Ukrainian
- Chinese (Simplified)
- Chinese (Traditional)


