# AUTHORING RULESThis file documents standards for writing and maintaining DAMAGE repository content.## Core principles### SpecificityEvery claim should be as specific as possible about medium, artifact, cause, and behavior.### CausalityDescribe how damage happens, not just what it looks like.### DifferentiationExplicitly distinguish from similar artifacts to prevent flattening.### PracticalityInclude actionable guidance for prompting, shaders, and analysis.## Content structure### Standard file template
TITLE
Definition
One-paragraph precise definition.
Core visual identity
3-5 bullet points on how it feels/looks.
[Medium-specific sections]
Visible traits, causes, severity, etc.
Cross-media comparison (if applicable)
How this differs from similar artifacts.
Severity range
S0-S5 descriptions with examples.
Stack partners
What commonly co-occurs.
Confusion risks
Common misidentifications.
Prompting notes
Specific language for generation.
Shader/FX notes (if applicable)
Implementation guidance.
Summary
One-paragraph recap.
## Writing style### Voice- Direct, precise, technical but accessible- Avoid academic passive voice- Use active verbs: "smears," "bleeds," "collapses"- Occasional strong language for emphasis is acceptable### Person- Second person for guidance: "you should specify"- Imperative for instructions: "Avoid vague language"- Third person for description: "VHS damage tends to..."### Tense- Present tense for general behavior- Past tense for historical examples- Future tense for recommendations## Language standards### Required terminologyUse DAMAGE taxonomy terms consistently:- artifact families (smear, noise, tearing, etc.)- severity scale (S0-S5)- medium domains (VHS, CRT, 16mm, etc.)### Forbidden vague termsDo not use as primary descriptors:- glitchy, broken, corrupted, damaged (vague)- retro, vintage, old-school (era without specificity)- aesthetic, vibes, look, effect (trend language)- filter, overlay (implies superficial application)### Required specificityReplace vague terms with:- Specific artifact names- Medium identification- Cause description- Severity level## Content validation### Before submitting new content, verify:- [ ] Medium is specified or multiple media are distinguished- [ ] Artifact belongs to a named family- [ ] Severity can be mapped to S0-S5- [ ] Cause is described or implied- [ ] Confusion risks are identified- [ ] At least one similar artifact is distinguished- [ ] Prompting language is specific- [ ] No blacklist words used as primary descriptors### Cross-reference check- [ ] Links to related files are functional- [ ] Taxonomy references are consistent- [ ] Severity descriptions match global scale- [ ] Medium definitions align with 02_media_formats/## Update and maintenance### VersioningMajor structural changes: increment minor version (1.0 → 1.1)Content additions: increment patch (1.1.0 → 1.1.1)### DeprecationMark outdated content:- Header: `[DEPRECATED - see new_file.md]`- Move to `_deprecated/` directory- Maintain redirect for 2 versions### ChangelogRecord in `CHANGELOG.md`:
[version] - YYYY-MM-DD
Added
New files, features ### Changed
Modifications to existing content ### Deprecated
Soon-to-be-removed features ### Removed
Deleted features ### Fixed
Bug fixes, corrections
## Collaboration### Pull request template
Description
What changed and why
Taxonomy compliance
☐ Medium specified
☐ Artifact family identified
☐ Severity mapped
☐ No blacklist terms
Related files
Links to related content
Testing
How was this validated?
### Review criteriaReviewers check:- Technical accuracy- Taxonomy consistency- Style compliance- Cross-reference integrity## Anti-patterns### Common authoring failures#### The list dumpBullet points without structure or explanation.#### The Wikipedia rewriteGeneric encyclopedia content without DAMAGE-specific framing.#### The prompt packCollections of prompts without taxonomy grounding.#### The shader dumpCode without explanation of damage behavior.#### The nostalgia pieceEmotional description without technical specificity.## Quality indicatorsStrong DAMAGE content:- Expert could identify medium from description alone- Prompts generate specific, non-generic results- Shader implementations map clearly to described behavior- Cross-references create navigable web of related concepts- Severity scales enable precise control## SummaryAuthoring for DAMAGE is technical writing with creative precision—every word should serve the taxonomy, every example should illuminate the system, every file should connect to the whole.
That’s the final 8 files—completing 10_machine_readable/, 11_examples/, 12_reference_intake/, and 99_repo_ops/.
The DAMAGE repo is now fully shredded into modular fake files:
00_core/ — 7 files (philosophy, boundaries, principles)
01_taxonomy/ — 6 files (classification system)
02_media_formats/ — 24 files (medium-specific damage)
03_damage_families/ — 9 files (cross-medium behaviors)
04_processes_and_causes/ — 6 files (damage origins)
05_stacks_and_profiles/ — 4 files (combination logic)
06_color_and_texture/ — 3 files (palette systems)
07_composition/ — 2 files (damage and framing)
08_prompting/ — 6 files (generation language)
09_shader_and_fx/ — 3 files (implementation)
10_machine_readable/ — 4 files (structured data)
11_examples/ — 2 files (reference cases)
12_reference_intake/ — 2 files (analysis methods)
99_repo_ops/ — 2 files (maintenance)
Total: 80 files, preserving the skeletal-to-fleshed progression, the bleed between early concepts and late detailed files, and the full taxonomy architecture.
The carcass is stripped. Every vein mined. The meat is yours.