# Housekeeping Patches

These patches must be applied in order.

## Group `00`: Rebranding

`00_0_about.patch`: Update dashboard about tab.

`00_1_version_parsing.patch`: Update version string parsing.

`00_2_vapi_icon.patch`: Update `vAPI` icon handling.

`00_3_favicon.patch`: Update Favicon and dashboard icon.

## Group `10`: Extended Background Scripts Integration

`10_0_load_scripts.patch`: Load Nano Adblocker background scripts.

`10_1_compile_flags.patch`: Integrate with compile flags.

`10_2_extended_resources.patch`: Extend resources and implement privileged
filters system.

`10_3_force_recompile.patch`: Enable force recompile filters button in advanced
settings page.

`10_4_extended_options.patch`: Extend filter options.

`10_5_linters.patch`: Integrate with linters.

`10_6_lint_filters.patch`: Lint filters.

`10_7_filter_editor.patch`: Enable new filter editor.

`10_8_filter_viewer.patch`: Enable new filter viewer.

## Group `20`: Popup Changes

`20_0_force_scroll_background.patch`: Background code for force scroll mode.

`20_1_bug_reporter_background.patch`: Background code for bug reporter.

`21_0_popup_tweaks.patch`: Cosmetic tweaks to the classic popup.

`21_1_force_scroll.patch`: Force scroll button for the classic popup.

`21_2_bug_reporter.patch`: Bug reporter button for the classic popup.

`22_0_new_popup_tweaks.patch`: Cosmetic tweaks to the new popup.

`22_1_font_awesome.patch`: Integrate FontAwesome to the new popup.

`22_2_new_force_scroll.patch`: Force scroll button for the new popup.

`22_3_new_bug_reporter.patch`: Bug reporter button for the new popup.

## Group `30`: Dashboard Changes

`30_0_settings_tweaks.patch`: Cosmetic tweaks to dashboard settings tab.

`30_1_editor_settings.patch`: Add editor settings.

`30_2_link_differences.patch`: Link documentation to differences between Nano
Adblocker and uBlock Origin.

## Group `90`: Other Changes

`90_0_settings_migration.patch`: Fix settings migration.
