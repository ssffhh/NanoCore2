# Important Announcements Regarding Recent Changes

Please read important announcements here: https://github.com/NanoAdblocker/NanoCore/issues/362

# Nano Core 2

Restarting fresh

A patch driven fork of uBlock Origin.

Upstream commit pin: `76eaef4d2b13bbc1b64d230182cac8f6523a9b17` or `1.27.10`

**Please submit issues to the
[Nano Core issues tracker](https://github.com/NanoAdblocker/NanoCore/issues).**

## Localization

Nano Core 2 has some extra locale strings, most of them are for Nano Linter.

You can contribute to localization here:
https://crowdin.com/project/nano-adblocker

Your language is not listed? Submit an issue to let me know.

## Setup

1. Install latest version of Git and Node.js.
1. In an appropriate directory, run:
   1. `git clone --depth 1 https://github.com/NanoAdblocker/NanoCore2.git`
   1. `git clone --depth 1 https://github.com/NanoAdblocker/NanoFilters.git`
   1. `git clone --depth 1 https://github.com/jspenguin2017/Edgyfy.git`
   1. `git clone --depth 1 https://github.com/jspenguin2017/uBlockProtector`
1. Run `git clone https://github.com/gorhill/uBlock.git` in an appropriate
   directory to get upstream. Check out a tag or commit as appropriate.
1. In Nano Core 2 repository:
   1. Navigate to `/term` directory and run `npm install`.
   1. Update `/config.nano.js` as appropriate.
   1. Run `node ./term` to open Nano Core 2 Terminal.

Note: The private repository `Prototype` is required for publishing.

## Development

You should not modify the upstream repository, instead, use Nano Core 2
Terminal to create and manage development environment.

```
reset    Delete development environment and create a fresh one using upstream
         repository, uncommitted changes in the fresh development environment
         will be cleared
apply    Apply all existing patches, in order, starting from the beginning
sync     Resynchronize all existing patches, in order, starting from the
         beginning
cont     Clear uncommitted changes and continue to resynchronize patches
         starting from the last one that failed or from the beginning as
         appropriate
mark     Create a patch based on the difference between tip of resynchronize
         patches and current code in development environment

make     Build extension from development environment
pack     Build, test, then package the extension
check    Check the syntax of files under the "/src" directory
publish  Build, test, package, then publish the extension
         Optionally pass browser name to publish for only one browser
clean    Remove all build files

lmake    Build English locale file from locale definition
lsync    Synchronize (non-English) locale files with the latest build of the
         Crowdin project
         This will not rebuild the Crowdin project even if there are changes

config   Print active configuration data
reload   Reload configuration data
exit     Exit the terminal
```

### Creating a New Patch

1. Run `mark`
1. Copy generated patch file to an appropriate directory
1. Give the new patch a good name
1. Add it to the README file
1. Add it to the configuration file
1. Run `reload` in the Terminal

### Renaming a Patch

1. Give the patch a new name
1. Update the README file
1. Update the configuration file
1. Run `reload` in the Terminal

### Removing a Patch

1. Delete the patch file
1. Update the README file
1. Update the configuration file
1. Run `reload` in the Terminal

## Version Update Checklist

1. Pull filters updates
1. If needed, pull upstream updates then update about string and commit pin
1. If needed, pull upstream updates to build scripts
1. If needed, pull upstream updates to `assets.json` and `manifest.json`
1. If needed, pull upstream updates to `1p-filters.js` and `asset-viewer.js`
1. If needed, build and pull locale updates
1. Bump version number
1. Perform [sanity tests](notes/sanity_tests.md)
1. Add tags to repositories, and upload packages
1. Upload packages to extension stores

## Version Update Extended Checklist

These are the potential problems to look out for:

1. Changes to development build detection logic
1. Changes to Font Awesome related CSS
1. Changes to image resources
   - Update build scripts to adapt
1. Changes to `/assets` directory structure
1. Changes to `scriptlets.js` format
   - Update build scripts and extended script snippets manifest to adapt
1. Changes to redirect declaration maps format in `redirect-engine.js`
   - Update `nano-background.js` to adapt
1. Renaming or removal of `messaging` and `popupData` variables in `popup.js`
   and `popup-fenix.js`
1. Changes to filters header parsing logic in `storage.js`
   - Update MirrorEngine to adapt
1. Changes to CNAME uncloaking Chromium support
   - Consider changing the default settings to disabled
1. Changes to local IP detection logic in `storage.js`
   - Update build scripts in NanoFilters and NanoMeow legacy server to adapt
1. Changes to filters syntax
   - Update NanoFilters, NanoContrib, and Nano Defender Integration to adapt
1. Changes to documented behaviors
   - Update documentations in NanoCore, NanoCore2, and NanoDoc to adapt

## Assets Manifest Update Checklist

1. When assets are removed
   - Open an issue in UltimateMirror to schedule removal of matching mirrored
     file
   - Remove the mirrored file after a few months
1. When assets that are enabled by default have changed
   - Update NanoFilters build scripts
   - Delete and refresh third party assets cache

## Subresource Integrity Incidence Response Protocol

When there is a severe issue with the content of a subresource, an intervention
can be easily placed with the help of
[UltimateMirror](https://github.com/NanoMeow/UltimateMirror) and
[MirrorEngine](https://github.com/NanoMeow/MirrorEngine):

1. Lock the subresource in UltimateMirror
1. Remove problematic content from UltimateMirror, if needed
1. Update `assets.json` so the sanitized subresource will be loaded from
   UltimateMirror

Later, the intervention can be lifted as follows:

1. Update `assets.json` as appropriate, the subresource should no longer be
   loaded from UltimateMirror
1. Wait a bit for cache to expire (takes about 10 minutes), then restart
   MirrorEngine
1. Unlock the subresource in UltimateMirror

## External Dependencies

1. Ace
   - `src-noconflict/ace.js` `15.04.20` (`1.4.10`)
   - `src-noconflict/ext-searchbox.js` `21.02.19`

## Tips

To update a patch, simply paste further changes to the bottom of that patch and
`sync` them in.

To fix conflict, either edit the broken patch file manually or disable it along
with patches after it then recreate the changes.
