# Custom HydroLearn OpenEDX theme
This is a custom theme to override the display of the HydroLearn instance of OpenEDX platform. This project includes overrides for the default templates used in openEDX for display of HydroLearn organization information on the home page and any template overrides for the LMS and CMS content.

# Branching Scheme
Maintaining organization through branch names to provide each release a raw/live copy

Though this naming has been varied previously, the updated intent for updating this repository is as follows:
- for new edx-platforms supported provide a named `raw/...` branch which provides an unmodified-from-platform version of the theme templates
  - e.g. for release tag `open-release/nutmeg.1` of the edx-platform, we generate a raw branch named `raw/nutmeg.1-theme` which modifies each template to exactly what is provided in edx-platform (literally copy-paste of the templates from the base repository, no customizations)
- next, we rebase the most recently generated theme onto this new `raw/` branch
  - e.g. for updating from `maple.2` to `nutmeg.1`: 
    1) create a new branch from existing live branch, checkout `live/maple.2-theme` -> NEW BRANCH -> `live/nutmeg.1-theme`
    1) rebase `live/nutmeg.1-theme` from `raw/maple.2-theme` to `raw/nutmeg.1-theme`
    
        `git rebase --onto raw/nutmeg.1-theme raw/maple.2-theme live/nutmeg.1-theme`
    1) work through merge conflicts, saving and commiting changes, then once complete publish  

this provides a direct comparison between branches which is useful for debugging during theme development.   

previously the branch naming was constantly changing between releases, but now we seek to maintain this naming convention to reduce confusion
