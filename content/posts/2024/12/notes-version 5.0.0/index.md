---
title: "Version 5.0.0"
aliases:
  - "darktable-5-0-0"
date: "2024-12-21"
featured: true
categories:
  - "actualites"
  - "featured"
tags:
  - "featured"
authors:
  - "jipivy"
coverImage: "images/dt_logo-5.0.0.png"
---

La version 5.0.0 de darktable est sortie samedi dernier.

Voici la traduction française des notes de version.

Merci à [Deepl](https://deepl.com/) pour l'aide précieuse.

<div align="right">Jean-Pierre Verrue</div>

___

Nous sommes fiers d'annoncer la nouvelle version de darktable, 5.0.0 !

La version github est disponible ici :
[https://github.com/darktable-org/darktable/releases/tag/release-5.0.0](https://github.com/darktable-org/darktable/releases/tag/release-5.0.0).

Comme toujours, n'utilisez pas le fichier tarball autogénéré fourni par
github, mais uniquement notre fichier tar.xz. Si vous ne construisez que pour vous-même
sans créer de paquetage pour une distribution quelconque, le clonage du code source
dans git est un moyen encore plus pratique.

Les sommes de contrôle sont :

```
$ sha256sum darktable-5.0.0.tar.xz
??? darktable-5.0.0.tar.xz
$ sha256sum darktable-5.0.0-x86_64.dmg
??? darktable-5.0.0-x86_64.dmg
$ sha256sum darktable-5.0.0-arm64.dmg
??? darktable-5.0.0-arm64.dmg
$ sha256sum darktable-5.0.0-win64.exe
??? darktable-5.0.0-win64.exe
```

Lors de la mise à jour à partir de la série stable 4.8, gardez à l'esprit que
vos modifications seront préservées pendant ce processus, mais que la nouvelle
bibliothèque et la configuration ne seront plus utilisables avec la version 5.0.0.
Il est fortement conseillé d'effectuer d'abord une sauvegarde.

#### Note importante :
Pour s’assurer que darktable supporte le format de fichier RAW de votre appareil
photo, veuillez lire [ce post](https://discuss.pixls.us/t/raw-samples-wanted/5420?u=lebedevri).
Vous y apprendrez comment contribuer à la constitution de l’ensemble d’échantillons
d’images (sous licence CC0) pour votre boîtier.

Depuis darktable 4.8 :

- ??? commits to darktable+rawspeed
- ??? pull requests handled
- ??? issues closed

_Veuillez noter que la documentation de darktable n'est pas encore complète pour la version 5.0
toutes les contributions sont très appréciées. Veuillez consulter la
[documentation du projet](https://github.com/darktable-org/dtdocs#contributing)
pour plus d'informations sur la manière de contribuer._

## Les grandes nouveautés

Voici un résumé des principales fonctionnalités ajoutées à darktable
5.0. Veuillez consulter le manuel de l'utilisateur pour plus de détails
sur les changements individuels (le cas échéant).

- Ce cycle de développement a inclus un grand nombre de changements qui
  améliorent l'expérience de l'utilisateur, comme le montre la section suivante.
  
## Améliorations de l'interface utilisateur (UI/UX)

- Added camera-specific styles for more than 500 camera models to more
  closely approximate the out-of-camera JPEG rendition.  These styles
  only affect contrast, brightness, and saturation and do not attempt
  to match sharpening, denoising, or hue shifts.  Also added a Lua
  script to auto-apply the appropriate style on import and manually
  apply styles to a collection of previously-imported images.

- Added an optional splash screen showing startup progress (including
  estimated time remaining during the scan for updated sidecar files) to
  dramatically reduce the time between invoking darktable and something
  appearing on screen when the user has a large library.

- The user interface now gives feedback while processing bulk image
  operations such as rating, tagging, applying styles, and edit
  history management (and undoing those operations), rather than
  silently freezing until the operation completes.  While the
  operation is in progress, darktable will now show either a busy
  cursor (such as a stopwatch or spinner) or a progress bar with
  option to cancel the remainder of the operation.

- Paths for drawn masks now display two Bézier handles per control point,
  which can be moved individually. This allows for more precise control
  of the paths.

- Added a high-contrast theme with bright white text on a dark gray
  background.

- Enhanced tooltips for utility module headers to provide more
  information about the module.

- Added more new-user hints on an empty lighttable.

- Added two new error placeholder images to distinguish between
  missing, unsupported, and corrupted images.  When attempting to edit
  such an image, an appropriate, more specific error message is
  displayed.

- When selecting a style in the export module, hovering on the style
  name in the popup menu displays a thumbnail previewing the effect of
  appending the style to the active image's edit (first selected image
  in lighttable, center-view image in darkroom).

- Allow for selecting the utility modules to be displayed on the
  panels in the different views.

  - Right-click on the empty panel area below the modules to get a
    menu where they can be hidden or shown. This allows additional
    modules to be added to the darkroom, like metadata editor and
    styles.

  - This replaces the options in the "collections" and "recently used
    collections" modules' preferences to show or hide the latter and
    show a "history" button in the former instead. Users that want the
    separate module will need to reenable it once via the new
    <kbd>Right-click</kbd> menu.

  - The menu also contains an option "restore defaults" that resets
    the selection and position of modules in the current view. In the
    preferences dialog, on the general tab, there's a "reset view
    panels" button that resets all views, including visibility and
    width of the panels themselves.

- Added a global preference to swap the left and right side panels in
  the darkroom view.

- The first time a new user presses Tab, they will be warned that this
  will hide all panels and how to get them back. Hopefully this
  prevents some confusion or frustration.

- Drag&drop utility module headers to reposition them across the left
  and right panels (lighttable) as well as vertically (all
  views). Hold <kbd>Ctrl+Shift</kbd> to avoid expanding/collapsing
  them before dragging. Each view can have a different layout.

- Drag&drop of processing modules in the darkroom right panel has been
  improved to auto-scroll when reaching the top or bottom and to not
  get confused when images get dragged into the area.

- Improved the message displayed at startup when the database is
  locked by another instance of darktable.

- Replaced the icon of the operator button in the color label filter
  for working with multiple selected color labels
  (union/intersection).

## Améliorations des performances

- Added OpenCL implementation of color equalizer.

- Improved the speed of bulk image operations by improving the speed
  of sidecar writes, and by moving sidecar updates for many operations
  into a background task, allowing the user to proceed before the
  writes complete.

- Significantly accelerated loading of PFM files due to loops
  parallelization and optimization that eliminated additional
  processing.

## Autres changements

- Switched default scope for new installations from histogram to
  waveform to display more detailed information about image color and
  tonality.

- The ISO 12646 color assessment condition is kept until unset by user
  action.

- Exposure bias can now be used to form collections and as a display filter.

- Improved visualization of the color equalizer's effect.

- Improved debugging support for verifying CPU vs. GPU results.

- Add Calibrite alias for X-Rite ColorChecker in color calibration.

- The scan for updated sidecar files now ignores timestamp differences
  of two seconds or less.

- The macOS installation package now has a background image to direct
  the user on installing darktable.app.

- Changed the user interface of the import dialog to make it easier to
  delete custom places.

- Numerous rounds of code cleanup.

- The copy-parts dialog does not select any module by default now.

- Add support for undo/redo for actions done on the filmstrip while in
  darkroom.

- In darkroom, add action (binding to <kbd>Ctrl+x</kbd> by default) for
  synchronizing the last edited module on current edited module to the
  selection.

- Adjusted the internal AVIF encoder parameter to significantly boost
  encoding speed without compromising the output quality.

- Tag names can now easily be copied to the clipboard via popup
  context menu in the tagging module.

- The Piwigo export storage now supports to specify a file name
  pattern for the exported file.

- The directory where darktable will write the log file under Windows
  has been changed to %USERPROFILE%\Documents\Darktable. This allows
  the user to easily see where the log file is located without even
  having to search for it in the documentation or FAQ. The previous
  location was deep in the system subdirectories of the user profile,
  and also under a hidden directory (so it was impossible to click to
  it in File Explorer with default system settings).

- Allow import of JPEG 2000 files with .jpf and .jpx file extensions.

- Add a visible indicator to the color calibration module when its
  color mapping section has non-neutral settings which will affect
  color rendition.

- Added new substitution variables `$(IMAGE.TAGS.HIERARCHY)` to insert
  tags with full hierarchy and `$(IMAGE.ID.NEXT)` to insert the image ID
  to be assigned to the image being imported, allowing the image ID to
  be part of the filename generated during a copy&import operation.

- Exporting to floating-point JPEG XL with a quality of 100 will try
  to do it as losslessly as possible. That is now consistent with the
  behavior of integral JPEG XL formats.

- Improved visibility of shortcuts that can be changed by users by
  using bold text.

- The histogram-exposure interface now supports all standard bauhaus
  features (<kbd>Ctrl+click</kbd>, <kbd>Right-click</kbd>...).

- Introduce image module order v5.0 to have the final-scale done before
  color-out to fix some issues with color difference between darkroom
  view and exported files.

- Add support for editing any live color-picker samples. Using
  <kbd>Right-click</kbd> on a sample it is possible to edit it
  (changing location and/or size of the box) and either add a new
  sample based on the edit or store the edit into an existing live
  sample.

- Added more substitution variables for using EXIF data fields,
  enabled autocompletion of variables in the watermark module.

  The new variables are `$(EXIF.FLASH)`, `$(EXIF.METERING)`,
  `$(EXIF.EXPOSURE.PROGRAM)`, `$(EXIF.WHITEBALANCE)` and
  `$(GPS.LOCATION.ICON)`.

- Increase maximum focal length for filtering auto-applied presets to
  2000mm.

- Added an expanded color-checker preset to the Color Look Up Table
  module with seven-level red/green/blue/gray ramps, IT8/CC24-like
  skin tones, and miscellaneous color patches for more targeted color
  adjustments across the full spectrum.

- Added support for EXIF tags 'AnalogBalance' used for color
  calibration and 'LinearResponseLimit' used in highlights
  reconstruction.

- If we find currently unsupported color calibration data in DNG
  specific tags, we tag the image by darktable|issue|no-samples for
  better support.

- Added support for HEIF files with AVC (H.264) compression and .avci
  file extension.

## Correction de bogues

- Fixed a performance regression for redrawing mipmaps.

- Fixed handling of old (2020) edits using Filmic RGB.

- Various OpenCL fixes to reduce differences between CPU and GPU
  processing: colorspace conversion, saturation gradient filter in
  color equalizer.

- Fixed gallery export not working on Windows.

- Fixed printer discovery in the print module, which could cause
  available printers to be missed.

- Work around out-of-spec EXIF date field caused by buggy software.

- Fixed reading embedded color profiles from PNG images.

- Fixed certain boundary cases in the crop module.

- Fixed crash when loading corrupted .gpx file in the geotagging module

- Fix preset handling in the export module not saving all parameters.

- Fix an issue in FilmicRGB where one of the parameter could be above
  the maximum allowed range making the validation failing and the
  whole set of parameters reset to default.

- Fix overlay recording to work in all cases (discarding history or
  copy/paste history for example) ensuring that an image not
  referenced anymore as overlay in a composite module can be removed.

- Properly reset darktable internal tag darktable|style|<name> and
  darktable|changed when resetting history.

- Fixed crash in the Piwigo export storage when not logged in to the
  Piwigo server.

- Fixed a bug in the export module where it was impossible to export a
  file again if "on conflict: overwrite if changed" was selected.

- Fixed a bug where double clicking on a label in darkroom modules
  does not reset the control.

- The composite module now prevents assigning an overlay that would
  lead to a loop. Previously, only direct references
  (image #1 <-> image #2) were checked; this has now been extended
  to also cover chains (image #1 -> image #2 -> image #3 -> image #1)
  of arbitrary length.

- Fix a bug in overlay module which incorrectly apply a color profile
  and so creating an unwanted and wrong color cast. This bug was a
  regression added just before the 4.8 release.

- Fixed a bug in color calibration module where switching between
  various illuminants could lead to unpredictable settings.

- Various fixes In the demosaic module. Non-usable options are hidden
  now. Fixed dual demosaicing for xtrans sensors and OpenCL code.

- Fixed a bug in the history module where style creation fails if a
  style with that name already exists.

- Fixed guides drawing in case a module is expanded and active.

- Ensure that the list of images in the culling view remains up to
  date when hidden.

- Fixed minor glitches in color calibration module.

- Fixed issues with wrong corrections in highlight opposed OpenCL
  code.

- Fixed surface blur radius calculation possibly resulting in garbled
  output.

## Lua

### API Version

- API version is now 9.4.0

### New Features

- Added new event, inter-script-communication, to permit sending messages
  from one running script to another running script.

- Added new function darktable.util.message(), for sending messages using
  the inter-script-communication event.

- Added new EXIF data fields to dt_lua_image_t:

  - exif_whitebalance

  - exif_flash

  - exif_exposure_program

  - exif_metering_mode

- Added new event, image-group-information-changed, that is raised any time
  an images group information changes.

### Bug Fixes

- Fixed a bug with dt_imageio_module_format_t.write_image so it returns
  true on success and false on failure.

### Add action support for Lua

### Other Lua changes

- Lua scripts are now better integrated into Darktable and can be
  fully translated. The design for the scripts manager has been
  reworked to be more in line with the current Darktable GUI modules.

## Notes

- When exporting to AVIF, EXR, JPEG XL, or XCF, selecting specific
  metadata (e.g. geo-tag or creator) is not currently possible. For
  AVIF, EXR, JPEG XL, and XCF formats, darktable will not include any
  metadata fields unless the user selects all of the checkboxes in the
  export module's preference options.

- Release 4.8 drops support for macOS versions older than 13.5.

## Changed Dependencies

### Mandatory

- Bump SQLite requirement to 3.26

### Optional

- n/a

## RawSpeed changes

- Fujifilm GFX cameras now use the vendor supplied crop

## Camera support, compared to 4.8

### Base Support

- ???

### White Balance Presets

- ???

### Noise Profiles

- ???

### Missing Compression Mode Support

- Apple ProRAW DNGs
- CinemaDNG lossless (Blackmagic, some DJI, etc.) and lossy (Blackmagic)
- DNG 1.7 using JPEG XL (Adobe enhanced, Samsung Expert RAW)
- Fujifilm lossy RAFs
- Nikon high efficiency NEFs
- OM System 14-bit high resolution ORFs
- Sony downsized lossless ARWs ("M" for full-frame, "S" for full-frame & APS-C)

### Suspended Support

Support for the following cameras is suspended because no samples are available on https://raw.pixls.us:

- Creo/Leaf Aptus 22(LF3779)/Hasselblad H1
- Fujifilm IS-1
- Kodak EasyShare Z980
- Leaf Aptus-II 5(LI300059)/Mamiya 645 AFD
- Leaf Credo 60
- Leaf Credo 80
- Minolta DiMAGE 5
- Olympus SP320
- Phase One IQ250
- Sinar Hy6/ Sinarback eXact
- ST Micro STV680

## Translations

- ???

