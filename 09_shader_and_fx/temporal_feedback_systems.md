# TEMPORAL FEEDBACK SYSTEMSThis file documents shader and FX techniques for temporal damage—artifacts that persist, echo, or evolve across frames.## DefinitionTemporal feedback systems use frame history to create persistence, trails, echoes, and memory-based damage effects.## Core techniques### Frame buffer feedbackStore previous frame output, blend with current input.```glsluniform sampler2D prevFrame;uniform float feedback;vec3 current = renderDamage();vec3 previous = texture(prevFrame, uv);vec3 output = mix(current, previous, feedback);
Controls: - feedback 0–1: persistence amount - 0.9 = long trails - 0.5 = medium echo - 0.1 = slight smear
Phosphor persistence simulation
Brightness-dependent feedback with exponential decay.
vec3 brightness = max(current, previous * decay);vec3 output = mix(current, brightness, luma(current) * persistence);
Models CRT phosphor: bright pixels persist longer.
Motion trail accumulation
Directional feedback based on motion vectors.
vec2 motion = getMotionVector(uv);vec3 previous = texture(prevFrame, uv - motion * scale);vec3 output = mix(current, previous, trailStrength);
Creates motion-smear without optical motion blur.
Datamosh-style prediction error
Intentionally “wrong” feedback—using stale motion or random displacement.
vec2 wrongMotion = motion * 0.5 + noise(time); // Corruptedvec3 wrongPrevious = texture(prevFrame, uv - wrongMotion);vec3 output = mix(current, wrongPrevious, 0.7);
Creates computational “memory error.”
Freeze-frame stutter
Periodic frame hold with blending.
float hold = floor(time / holdDuration) * holdDuration;vec3 frozen = texture(frameAtTime(hold), uv);vec3 output = mix(current, frozen, stutterAmount);
Creates buffering/playback failure effect.
Advanced temporal systems
Multi-frame history
Store N previous frames for: - Multi-frame ghosting - Echo patterns - Temporal filtering
Implementation: Texture array or ring buffer of frame textures.
vec3 echo = vec3(0);for (int i = 0; i < NUM_FRAMES; i++) {    float weight = pow(decay, float(i));    echo += texture(frameHistory[i], uv) * weight;}
Temporal noise evolution
Noise that evolves coherently across frames.
// 3D noise: x, y, timefloat noise = snoise(vec3(uv * scale, time * evolution));
Prevents “crawling” while maintaining change.
Adaptive feedback
Feedback amount varies by image content.
float localFeedback = baseFeedback * (1.0 - edgeDetect(uv));// Less feedback on edges (sharper), more in flat areas (smear)
Temporal artifacts and their systems
Artifact
Technique
Key Parameter
Phosphor trails
Brightness feedback
Decay rate
Motion smear
Motion vector feedback
Trail length
Frame echo
Periodic frame hold
Hold duration
Ghost frames
Multi-frame blend
Frame count
Prediction error
Corrupted motion
Error amount
Freeze stutter
Conditional hold
Stutter probability
Performance considerations
Memory
Frame buffers are expensive: - Minimize resolution where possible - Use RGB8 instead of RGB16 if quality allows - Share buffers between effects
Bandwidth
Reading previous frames costs: - Sample sparingly - Use lower resolution for feedback - Consider tiled or sparse sampling
Latency
Feedback creates one-frame latency: - Acceptable for damage effects - Problematic for gameplay-critical rendering
Integration with DAMAGE taxonomy
Temporal/memory artifacts family
All techniques in this file map to: - Phosphor trails - Frame ghosts - Motion echoes - Persistence artifacts - Freeze/repeat loops
Severity mapping
Severity
Feedback
Decay
Additional
S1
0.1
0.9
Minimal
S2
0.3
0.8
Subtle
S3
0.5
0.7
Clear effect
S4
0.7
0.5
Dominant
S5
0.9
0.3
Overwhelming
Summary
Temporal feedback systems are memory made visible—previous frames refusing to disappear, creating the persistence, trails, and ghosts that make damage feel alive through time.
---**FILE: `DAMAGE/10_machine_readable/damage_taxonomy.json`**```json{  "taxonomy_version": "1.0.0",  "taxonomy_name": "DAMAGE Cross-Media Damage Taxonomy",    "structure": {    "core_principles": [      "medium_specificity",      "cause_awareness",      "behavior_over_vibe",      "stack_logic",      "legibility_matters"    ],        "classification_axes": [      "medium",      "artifact_family",      "cause",      "severity",      "stack_behavior"    ]  },    "medium_domains": {    "analog_video": {      "id": "AV",      "formats": ["VHS", "Betamax", "U-matic", "Hi8"],      "native_artifacts": ["chroma_bleed", "tracking_error", "head_switching", "luma_softness"]    },    "crt_display": {      "id": "CRT",      "native_artifacts": ["raster", "phosphor_bloom", "phosphor_trails", "convergence_error"]    },    "digital_video": {      "id": "DV",      "codecs": ["H.264", "H.265", "VP9", "AV1"],      "native_artifacts": ["macroblocking", "banding", "mosquito_noise", "temporal_smear"]    },    "film": {      "id": "FILM",      "formats": ["8mm", "16mm", "35mm", "70mm"],      "native_artifacts": ["grain", "gate_weave", "halation", "scratches", "light_leaks"]    },    "photography_optical": {      "id": "OPT",      "native_artifacts": ["lens_flare", "chromatic_aberration", "bokeh", "diffraction"]    },    "camera_sensor": {      "id": "SENS",      "types": ["CCD", "CMOS"],      "native_artifacts": ["noise", "rolling_shutter", "blooming", "dead_pixels"]    },    "print_scan_xerox": {      "id": "PRINT",      "native_artifacts": ["toner_drag", "misregistration", "dot_screen", "scanner_bands"]    }  },    "artifact_families": {    "noise": {      "id": "F01",      "description": "Distributed signal variation",      "members": ["grain", "static", "snow", "speckle", "chatter"]    },    "smear_drag_bleed": {      "id": "F02",      "description": "Directional information spread",      "members": ["chroma_bleed", "motion_smear", "tape_smear", "optical_smear"]    },    "tearing_sync_instability": {      "id": "F03",      "description": "Frame and timing disruption",      "members": ["horizontal_tear", "vertical_roll", "jitter", "sync_loss"]    },    "compression_breakage": {      "id": "F04",      "description": "Codec and quantization artifacts",      "members": ["macroblocking", "banding", "mosquito_noise", "ringing"]    },    "surface_contamination": {      "id": "F05",      "description": "Physical matter interference",      "members": ["dust", "scratches", "hair", "fingerprints", "stains"]    },    "light_exposure_failure": {      "id": "F06",      "description": "Brightness and exposure issues",      "members": ["clipping", "bloom", "halation", "light_leaks"]    },    "color_failure": {      "id": "F07",      "description": "Color channel issues",      "members": ["misalignment", "channel_dropout", "false_color", "cast_shift"]    },    "geometry_failure": {      "id": "F08",      "description": "Spatial deformation",      "members": ["warping", "curvature", "skew", "rolling_shutter"]    },    "temporal_memory_artifacts": {      "id": "F09",      "description": "Time-based persistence",      "members": ["afterimages", "ghost_frames", "motion_echoes", "trails"]    }  },    "severity_scale": {    "S0": {"name": "none", "description": "No visible artifact"},    "S1": {"name": "trace", "description": "Barely perceptible"},    "S2": {"name": "mild", "description": "Present but restrained"},    "S3": {"name": "moderate", "description": "Clearly visible, active"},    "S4": {"name": "severe", "description": "Strongly disruptive"},    "S5": {"name": "catastrophic", "description": "Image collapse"}  },    "stack_types": {    "native": "Artifacts naturally co-occurring in one medium",    "causal": "Artifacts from single underlying cause",    "chain": "Artifacts accumulated through transfer sequence",    "hybrid": "Deliberate cross-medium combination"  },    "prompt_assembly": {    "structure": "[medium] + [artifact] + [severity] + [cause]",    "example": "VHS + chroma_bleed + S3 + worn_tape"  }}