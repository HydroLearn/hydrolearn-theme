# Custom HydroLearn OpenEDX theme

This is a custom theme to override the display of the HydroLearn instance of OpenEDX platform. This project includes overrides for the default templates used in openEDX for display of HydroLearn organization information on the home page and any template overrides for the LMS and CMS content.

# Branching Scheme

Maintaining organization through branch names to provide each release a raw/live copy

`master` is expected to be maintained as the `raw` files used in the theme kept up to date with the latest implemented release.

- so a pull request for the latest `raw` branch into `master` is expected to be generated each time

---

## Update process

### Create a new Raw branch

from the latest up to date version of `master`, create a new `raw` branch for the release being updated to

e.g. when updating to `edx-platform` release `open-release/VERSION_NAME`:

1. generate branch from master named `raw/VERSION_NAME`
1. for each file in the theme, copy the raw files from `open-release/VERSION_NAME` (literally copy-paste of the templates from the edx-platform repository, no customizations)
1. push these changes to the `raw/VERSION_NAME` branch (goal being that if this raw branch is built it will be identical to if there was no custom theme at all)

### Generate the new live branch

1. from the branch generated in the previous section, `raw/VERSION_NAME`, generate a new branch `live/VERSION_NAME`
1. perform a cherry-pick of all changes that were done with the previous `raw/...` & `live/...` branches

e.g. for updating from `maple.2` to `nutmeg.1`:

1. be sure you're on the new branch being updated
   - `git checkout live/nutmeg.1`
1. perform cherrypick of all changes done between the old version's raw -> live versions
   - `git cherry-pick raw/maple.2-theme..live/maple.2`
1. work through merge conflicts, saving and commiting changes, then once complete publish
1. at this point, you will need to build the application with the new theme, and work through any issues manually
   - unfortunately, this is a tedious process requiring numerious builds of the application to suss out necessary additions needed, additional theme templates/styles needed, etc.

This is not a fool-proof process, but it does maintain at least some order when updating these directly overlayed files and provides a direct comparison between modified/unmodified which is useful for debugging during theme development.
