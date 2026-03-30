# FILE NAMING RULESThis file documents standardized naming conventions for all DAMAGE repository files.## Core principles### Machine-readableNames should work in URLs, command lines, and scripts without escaping.### Human-readableNames should indicate content without opening the file.### SortableNames should order logically in directory listings.### ConsistentSame type of content, same naming pattern.## General rules### Characters- Use: lowercase a-z, 0-9, underscore _- Avoid: spaces, hyphens (except as noted), special characters, uppercase### Structure
[category_prefix]_[descriptive_name].[extension]
### Length- Maximum: 50 characters (excluding extension)- Target: 30-40 characters## Directory-specific rules### 00_core/
[topic].md
Examples:- `damage_definition.md`- `scope_and_boundaries.md`- `anti_drift.md`### 01_taxonomy/
[topic].md
Examples:- `master_taxonomy.md`- `severity_scale.md`- `artifact_stack_logic.md`### 02_media_formats/[medium]/
[specific_artifact].md
Examples:- `vhs_damage.md`- `crt_scanlines_and_raster.md`- `film_grain_profiles.md`### 03_damage_families/[family]/
[specific_behavior].md [family_name]_family_map.md
Examples:- `smear_types.md`- `noise_family_map.md`- `horizontal_tearing.md`### 04_processes_and_causes/
[cause_description].md
Examples:- `physical_handling_damage.md`- `heat_age_and_storage_damage.md`- `re_recording_and_duplication_loss.md`### 05_stacks_and_profiles/
[profile_type].md
Examples:- `medium_true_profiles.md`- `hybrid_damage_profiles.md`- `severe_failure_stacks.md`### 06_color_and_texture/
[topic].md
Examples:- `damage_palette_logic.md`- `heat_burn_palettes.md`- `sickly_digital_palettes.md`### 07_composition/
[topic].md
Examples:- `how_damage_affects_composition.md`- `focal_point_obscuration.md`### 08_prompting/
[topic].md
Examples:- `damage_prompting_principles.md`- `medium_specific_prompt_phrases.md`- `damage_intensity_ladder.md`### 09_shader_and_fx/
[topic].md
Examples:- `shader_translation_guide.md`- `temporal_feedback_systems.md`### 10_machine_readable/
[topic].[json|csv]
Examples:- `damage_taxonomy.json`- `medium_effect_matrix.csv`- `severity_scale.json`### 11_examples/
[topic].md
Examples:- `example_damage_profiles.md`- `before_after_logic.md`### 12_reference_intake/
[topic].md
Examples:- `how_to_analyze_references.md`- `intake_template.md`### 99_repo_ops/
[topic].md
Examples:- `file_naming_rules.md`- `authoring_rules.md`## Special cases### Index filesNamed `README.md` in each directory.### Root files
DAMAGE_description.[md|json|csv]
Examples:- `DAMAGE_REPO_STRUCTURE.md`- `DAMAGE_MANIFESTO.md`### Deprecated/movedPrefix with underscore: `_old_filename.md`### DraftsPrefix with `DRAFT_`: `DRAFT_new_artifact.md`## Anti-patterns### Bad examples- `VHS Damage.md` (space, uppercase)- `vhs-damage.md` (hyphen, inconsistent)- `glitch_stuff.md` (vague)- `02_media_formats/analog_video/VHS.md` (too short, not descriptive)- `very_long_descriptive_name_that_goes_on_forever.md` (too long)### Good examples- `vhs_damage.md`- `chroma_luma_failures.md`- `artifact_stack_logic.md`- `damage_intensity_ladder.md`## Automated validationScripts should check:- [ ] Lowercase only- [ ] No spaces- [ ] Underscores only for separation- [ ] No special characters- [ ] Appropriate extension- [ ] Length under 50 chars- [ ] No reserved words (CON, PRN, etc. on Windows)## SummaryConsistent naming is the foundation of navigable taxonomy—every filename should be a clear signpost to its content.