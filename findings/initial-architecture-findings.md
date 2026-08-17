# Initial Architecture Findings

**Research program:** R-004 Luna Vision Assistive Computer Vision Research  
**Date:** 2026-08-16  
**Evidence status:** Literature-supported engineering synthesis

## Finding 1: Luna Vision should be modular, stateful, and observable

The initial research does not support a design where one multimodal model watches a video stream and directly controls all navigation behavior. The stronger design separates perception, localization, mapping, planning, semantic reasoning, and feedback.

The reason is testability as much as capability. If depth, localization, mapping, and language are separate components, each can be benchmarked, compared, replaced, and allowed to fail explicitly.

**Engineering implication:** Luna should expose a structured internal state rather than only natural-language output.

## Finding 2: The conversational layer should explain measured state, not replace it

Multimodal models are useful for scene descriptions, user questions, and semantic interpretation. However, BLV-focused datasets such as GuideDog and EgoBlind still show meaningful gaps in depth reasoning, accessibility-aware guidance, and user-intent understanding.

**Engineering implication:** the language layer should receive structured inputs such as current pose, pose confidence, tracked objects, measured or estimated distance, OCR results, route state, and hazard flags. If those inputs are uncertain, the answer should remain uncertain.

## Finding 3: Persistent spatial memory is central to the Luna concept

A useful assistive system should not rebuild the world from scratch on every frame. Rooms, doors, stable objects, route structure, and previously mapped geometry need persistence across time and sessions.

**Engineering implication:** object and place records should include stable identifiers, approximate pose, semantic class, confidence, and freshness information. Movable objects must be distinguishable from stable landmarks.

## Finding 4: Floor-plan anchoring is a high-value research direction

PALMS and PALMS+ are unusually close to Luna's intended indoor workflow because they investigate localization against known floor plans without requiring installed beacons.

**Engineering implication:** reproduce or benchmark floor-plan localization early enough to determine whether a mapped home can serve as a stable coordinate frame across restarts and tracking loss.

## Finding 5: Monocular depth is useful, but should be challenged by direct depth sensing

Modern monocular depth models make relative depth accessible without specialized sensors. Depth Anything V2 is a strong prototype candidate. But the safety question is not whether the output looks convincing. The important question is how often it fails on hazards that matter.

**Engineering implication:** compare monocular depth against LiDAR or RGB-D reference data where possible and report performance by material, lighting, motion, distance, and hazard type.

## Finding 6: Geometry should remain useful even when semantics fail

A system that recognizes only known classes can miss an unfamiliar obstacle. Traversability and obstacle logic should therefore use geometry in addition to object labels.

**Engineering implication:** an unknown object blocking traversable space should still be able to trigger a hazard state.

## Finding 7: Failure detection is a first-class subsystem

Tracking loss, stale sensor frames, map disagreement, uncertain depth, and localization ambiguity are normal operating conditions in real vision systems.

**Engineering implication:** Luna should maintain explicit operating states such as:

- `NORMAL`
- `AWARENESS_ONLY`
- `LOW_CONFIDENCE`
- `LOCALIZATION_LOST`
- `SENSOR_STALE`
- `STOP_GUIDANCE`

The system should be allowed to abstain.

## Finding 8: Accessible feedback must manage information density

More information is not always better. Urgent movement or obstacle cues need to remain distinguishable from descriptive speech.

**Engineering implication:** test progressive information density, where urgent signals are brief and prioritized while richer description is available on demand. Speech, spatial audio, haptics, and low-vision visual overlays should be evaluated as separate channels and in combinations.

## Finding 9: Wearable hardware should follow architecture validation

The research supports starting with a smartphone and offboard PC rather than prematurely optimizing around a hat-sized compute platform.

**Engineering implication:** measure compute, latency, bandwidth, power, sensing, and thermal needs first. Hardware miniaturization can then be based on actual requirements.

## Finding 10: Luna needs failure-focused data, not only successful examples

Conventional benchmark datasets are necessary but insufficient for an assistive navigation system.

**Engineering implication:** future Luna-specific data collection should deliberately include blank walls, mirrors, reflective and transparent surfaces, low light, motion blur, repeated rooms, moved furniture, tracking loss, unexpected obstacles, stale maps, and re-localization attempts.

## Current Architectural Baseline

```text
Camera + IMU
    |
    v
Capture / calibration / telemetry
    |
    +--> Depth / obstacle / traversability
    |
    +--> VIO / SLAM / pose confidence
    |
    +--> Object / text / product recognition
    |
    v
Persistent spatial memory / map
    |
    +--> Floor-plan anchor / re-localization
    |
    v
Route + interaction planner
    |
    v
Structured system state
    |
    +--> Safety / uncertainty controller
    |
    +--> Conversational semantic layer
    |
    v
Speech / audio / haptic / visual feedback
```

This is a research baseline, not a locked product architecture. Each layer should remain replaceable as experiments produce stronger evidence.

## Next Validation Priorities

1. Build synchronized phone-camera and IMU capture.
2. Establish ORB-SLAM3 and OpenVINS benchmark baselines.
3. Benchmark Depth Anything V2 on indoor hazard-focused scenes.
4. Create replayable test sequences with known failure cases.
5. Prototype persistent room/object state.
6. Reproduce or adapt PALMS/PALMS+ floor-plan localization concepts.
7. Define shared confidence and subsystem-health messages before adding navigation guidance.
