# Luna Vision State of the Field

**Research program:** R-004 Luna Vision Assistive Computer Vision Research  
**Date:** 2026-08-16  
**Evidence status:** Literature-supported synthesis

## Executive Summary

The current research landscape supports Luna Vision as a staged research and engineering program, but not as a single vision-language model that watches a camera and directly issues safety-critical navigation instructions.

The strongest architecture supported by the initial review is modular and stateful. Dedicated subsystems should handle geometry, localization, persistent spatial memory, semantic recognition, route logic, accessible feedback, and system health. A conversational model can sit above those systems to answer questions and explain state, but should not invent missing geometry or replace measured localization and depth.

Several parts of this architecture are already practical enough to prototype. Phone-camera plus inertial localization has strong research precedent. Open-source VIO and SLAM systems are available. Persistent mapping and simulation platforms are mature enough for controlled experiments. Navigation-oriented accessibility datasets now include first-person video, depth, dense labels, and blind-user questions. At the same time, recent BLV-focused work continues to show weaknesses in depth reasoning and accessibility-aware scene guidance, which is a major reason to keep the conversational layer separate from safety-critical perception.

## What Appears Feasible Now

### Phone-first sensing

A smartphone camera and IMU provide a practical starting sensor package. Early prototypes can stream synchronized camera and inertial data to a PC so perception and localization can be evaluated before power, thermal, and miniaturization constraints dominate the design.

### Visual-inertial localization and SLAM

ORB-SLAM3 and OpenVINS provide strong open research baselines for pose estimation and motion tracking. RTAB-Map provides a useful route toward persistent appearance-based mapping and occupancy or semantic-map experiments.

### Floor-plan localization

PALMS and PALMS+ are especially relevant because they investigate infrastructure-free indoor localization against a known floor plan. This is closely aligned with Luna's goal of mapping a home or other indoor space and later re-localizing against that persistent representation.

### Depth and obstacle perception

Monocular depth estimation is practical enough to benchmark immediately. Depth Anything V2 is a particularly useful candidate. However, monocular depth should be treated as an experimental component rather than assumed to be a safety ground truth. Direct depth sensing should remain an important comparator.

### Simulation and controlled evaluation

Habitat and HM3DSem make it possible to stress-test route logic, semantic memory, and mapping without putting a person at risk. Simulation success is not equivalent to real-world safety, but it is a valuable intermediate stage.

### Accessibility-aware scene understanding

SANPO, EgoBlind, and GuideDog materially improve the research landscape by providing navigation-oriented scenes, blind-user questions, depth-related evaluation, and accessibility-aware guidance tasks.

## Major Research Gaps

### Hazard reliability

A single monocular camera cannot currently be assumed to detect every important hazard in arbitrary environments. Transparent, reflective, thin, overhanging, low-contrast, and fast-moving hazards remain important stress cases.

### Persistent semantic memory

Robotics mapping can preserve geometry, but a human-centered assistive world model needs additional logic. Luna must decide which objects deserve persistent identity, how to track movable objects, how to mark stale information, and how to communicate uncertainty when the environment changes.

### Confidence and graceful degradation

A navigation-capable system needs explicit failure states. Tracking loss, stale sensor input, uncertain depth, map disagreement, and low-confidence localization should change what Luna is allowed to tell the user. A system should be able to fall back from guidance to awareness-only behavior instead of remaining confidently wrong.

### Human-centered route quality

Shortest-path planning is not enough. Accessible route cost may need to account for stairs, narrow passages, temporary obstacles, visual uncertainty, crowd density, surface conditions, and user preferences.

### BLV-specific data

No single public dataset appears to cover the complete Luna task. Future work will likely require controlled Luna-specific sequences that combine synchronized video, IMU, pose or depth reference, indoor geometry, blind-user questions, obstacles, map state, and navigation outcomes.

## Recommended Modular Architecture

1. **Sensor and capture layer** - synchronized camera, IMU, calibration, timestamps, and telemetry.
2. **Geometry and safety perception** - depth, obstacle, traversability, segmentation, and object tracking.
3. **Localization and motion state** - VIO and SLAM with explicit confidence and tracking-loss behavior.
4. **Persistent spatial memory** - rooms, doors, stable objects, occupancy or topology, timestamps, and confidence.
5. **Floor-plan anchoring and re-localization** - persistent coordinate system and recovery after restart or tracking loss.
6. **Route and interaction planner** - traversable-space or graph-based planning with dynamic obstacle handling.
7. **Semantic and conversational layer** - questions and explanations grounded in structured system state.
8. **Accessible feedback layer** - speech, spatial audio, haptics, and low-vision overlays where useful.
9. **Safety and observability layer** - system health, freshness, disagreement, uncertainty, and abstention states.

## Suggested Evaluation Gates

The system should advance through measured gates rather than demo quality alone.

**Localization:** trajectory error, tracking uptime, loss duration, re-localization success, recovery time, covariance or confidence behavior.

**Depth:** error, temporal stability, material-specific failure analysis, and consistency under low light, reflections, motion blur, and texture-poor scenes.

**Obstacle safety:** hazard recall by distance, false-negative rate, false-stop rate, minimum detection distance, time-to-collision error, and end-to-end latency.

**Mapping:** map drift, object-placement error, stale-object rate, topology accuracy, and recovery after restart.

**Semantic and OCR:** precision, recall, OCR error rate, barcode success time, dense-shelf detection recall, and product-match confidence.

**System performance:** p50/p95/p99 latency, dropped frames, CPU/GPU/RAM use, network interruption behavior, thermal throttling, and power use.

**Human-centered controlled testing:** route completion, wrong turns, interventions, near misses in safe setups, workload, comprehension, trust calibration, and user preference.

## Development Progression

- **Phase 0:** synchronized phone-camera and IMU capture to PC
- **Phase 1:** independent perception benchmarks
- **Phase 2:** VIO and SLAM benchmarks
- **Phase 3:** persistent room and object model
- **Phase 4:** floor-plan anchored controlled navigation
- **Phase 5:** accessible guidance and grounded conversation
- **Phase 6:** OCR, signage, barcode, and product interaction
- **Phase 7:** staged real-world controlled trials with explicit safety review
- **Later:** wearable miniaturization after the compute, sensing, latency, and thermal requirements are measured

## Important Boundary

The research supports building and testing these components. It does **not** support claiming that current prototypes are safe for independent mobility. Awareness assistance, experimental route guidance, and validated mobility support are different levels of evidence and should remain clearly separated.

## Key Sources

- SANPO: https://google-research-datasets.github.io/sanpo_dataset/
- EgoBlind: https://github.com/doc-doc/EgoBlind
- GuideDog: https://aclanthology.org/2026.acl-long.251/
- Project Guideline: https://sites.research.google/guideline/
- Depth Anything V2: https://github.com/DepthAnything/Depth-Anything-V2
- ORB-SLAM3: https://github.com/UZ-SLAMLab/ORB_SLAM3
- OpenVINS: https://docs.openvins.com/
- RTAB-Map: https://github.com/introlab/rtabmap
- PALMS / PALMS+: https://github.com/Head-inthe-Cloud/PALMS-Plane-based-Accessible-Indoor-Localization-Using-Mobile-Smartphones
- TUM Visual-Inertial Dataset: https://cvg.cit.tum.de/data/datasets/visual-inertial-dataset
- Habitat: https://aihabitat.org/

## Provenance

This public summary is derived from the R-004 research landscape and technical source inventory maintained in the private Luna research workspace. It is a synthesis of cited research, not a claim that all listed systems have already been reproduced inside Luna.
