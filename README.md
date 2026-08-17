# Luna Vision Research

**Public research and development toward reliable real-time assistive computer vision for blind and low-vision users.**

> ## What this repository is
> Luna Vision Research documents an **ongoing R&D process**, not a claim that the full Luna Vision system has already been built or validated. It contains literature-backed research, engineering hypotheses, architecture proposals, reproduction plans, experiments, and eventually benchmarked implementations and controlled field evaluations.
>
> **A capability described in this repository should not be assumed to exist in Luna unless it is explicitly labeled IMPLEMENTED.** Research findings describe what the evidence suggests should be built and tested.

## Current maturity

**Program stage: RESEARCH + ARCHITECTURE**

The current R-004 program is primarily gathering evidence, identifying reproducible technical baselines, defining system architecture, acquiring research resources, and designing measurable experiments. Some underlying technologies are mature or reproducible upstream, but that does **not** mean Luna has reproduced, implemented, benchmarked, or field-tested them yet.

### R&D status vocabulary

| Status | Meaning |
| --- | --- |
| **RESEARCHED** | Supported by literature, primary sources, datasets, or technical investigation. |
| **PROPOSED** | A Luna-specific architecture, method, or engineering solution has been designed but not yet implemented. |
| **REPRODUCTION PLANNED** | An upstream result/system has been selected for independent reproduction. |
| **REPRODUCED** | The relevant upstream experiment or capability has been independently run within the Luna research workflow. |
| **IMPLEMENTED** | The capability exists in a Luna prototype. |
| **BENCHMARKED** | The Luna implementation has been measured against defined metrics/test conditions. |
| **FIELD TESTED** | The implementation has undergone documented controlled real-world evaluation. |

These labels are intentionally conservative. Progression is expected to look like:

`RESEARCHED → PROPOSED / REPRODUCTION PLANNED → REPRODUCED → IMPLEMENTED → BENCHMARKED → FIELD TESTED`

Not every research direction will progress through every stage. Negative results and abandoned approaches are valid R&D outcomes and should be documented when useful.

## Project goal

Luna Vision explores how computer vision, spatial computing, localization, OCR, multimodal systems, and accessible interaction could support practical environmental understanding for blind and low-vision users.

The development strategy begins with instrumented PC and phone-camera prototypes. Wearable hardware is a later-stage target after the underlying perception, localization, mapping, uncertainty, and interaction problems are better understood.

## R-004: Luna Vision Assistive Computer Vision Research

**Current status: RESEARCHED / ARCHITECTURE PROPOSED**

R-004 is investigating what would actually be required to build a reliable real-time assistive computer-vision system rather than beginning with an assumption that a single AI model can solve the problem.

Research areas include:

1. Egocentric computer vision and scene understanding
2. Object detection and segmentation
3. Monocular, stereo, and sensor-based depth estimation
4. Obstacle and traversability detection
5. Visual-inertial odometry and SLAM
6. Indoor localization and re-localization
7. Persistent spatial memory and world models
8. Floor-plan localization and indoor mapping
9. Accessible route planning and navigation
10. OCR, signage, barcode, label, and product recognition
11. Retail navigation and shelf understanding
12. Multimodal interaction and accessible feedback
13. Real-time inference, latency, and edge deployment
14. Reliability, uncertainty, failure detection, and safety
15. Evaluation methods centered on blind and low-vision use cases

## Current research direction

The strongest architectural conclusion from the initial landscape work is that Luna should be investigated as a **modular, stateful system** rather than as one vision-language model directly converting camera frames into navigation instructions.

The proposed research architecture separates:

- sensor capture and synchronization
- geometry, depth, obstacles, and traversability
- visual-inertial localization and SLAM
- persistent spatial memory
- floor-plan anchoring and re-localization
- route planning
- semantic recognition, OCR, and product understanding
- conversational reasoning grounded in measured state
- accessible feedback
- uncertainty, health monitoring, and graceful degradation

**Status: PROPOSED.** This is an architecture derived from the research landscape. It is not a claim that the complete stack has been implemented.

## What exists here today

The public repository currently contains:

- **RESEARCHED:** a state-of-the-field review across the major Luna Vision technical problems
- **RESEARCHED:** a curated high-value technical source map
- **PROPOSED:** initial Luna-specific architecture findings and engineering implications
- **DEFINED:** public research methodology, evidence rules, and publication boundaries
- **PLANNED:** reproducibility, experiments, benchmarks, and implementation work as R-004 advances

When experimental work begins, each result should identify its exact maturity rather than silently changing a research claim into an implementation claim.

## Repository structure

- `research/` - literature reviews, technology landscape work, and source maps
- `findings/` - synthesized conclusions and engineering implications
- `experiments/` - reproducible experiments and prototype investigations
- `benchmarks/` - evaluation methodology and benchmark results
- `architecture/` - proposed system architecture and design decisions
- `reproducibility/` - instructions and records needed to reproduce findings
- `docs/` - supporting public documentation

## Research philosophy

The goal is not simply to make a camera describe an image. A useful assistive system may need to maintain context over time, understand spatial relationships, distinguish hazards from irrelevant objects, recognize uncertainty, and communicate information without overwhelming the user.

The research therefore treats Luna Vision as a system-level problem involving perception, localization, memory, reasoning, human-computer interaction, accessibility, and safety.

A core principle is to separate **evidence from interpretation**. Published literature can justify investigating a method. Reproduction can show that a result can be obtained in the Luna research environment. Implementation can show that the method runs in Luna. Benchmarking can measure how well it performs. Controlled field evaluation is required before making claims about real-world assistive performance.

## Safety and scope

Assistive navigation is safety-sensitive. Experimental perception can be incomplete, delayed, or incorrect. Nothing in this repository should be interpreted as evidence that an unvalidated prototype is safe for independent mobility.

Luna Vision is being investigated as an assistive layer, not as justification for removing established mobility tools such as canes, guide dogs, or appropriate orientation and mobility techniques.

Failure cases are first-class research results. Tracking loss, uncertain depth, stale maps, sensor failures, model disagreement, and situations where the system should abstain are part of the research problem rather than edge cases to hide.

## Public research boundary

This repository is intentionally public-facing. Appropriate material includes research summaries, citations, architecture proposals, benchmark methodology, reproducible code, aggregate experimental results, negative findings, and other material useful to researchers, developers, accessibility practitioners, and prospective employers.

Private user data, credentials, private imagery, personally identifying information, proprietary datasets without redistribution rights, and sensitive internal material should not be committed here.

See [`PUBLICATION_POLICY.md`](PUBLICATION_POLICY.md) for the publication rules.

## Long-term research questions

A mature system would need evidence showing whether it can reliably support questions such as:

- What is immediately around the user?
- Is there an obstacle or drop-off in the path?
- Where is a doorway, counter, aisle, or destination?
- What sign, package, product, or label is visible?
- Has the system observed this location before?
- Can the current camera pose be localized against a persistent indoor map?
- Which route is appropriate given accessibility constraints and uncertainty?
- When should the system refuse to provide guidance because its confidence is insufficient?

These are **research targets**, not current capability claims.

## Follow the R&D process

This repository is intended to remain useful even before field testing. The public record will progressively show:

`question → evidence → design decision → reproduction → prototype → benchmark → failure analysis → revision → controlled evaluation`

The objective is to make both the eventual solution **and the process used to reach it** inspectable.

## Project status

**Active R&D, August 2026. Current phase: research landscape, architecture, source acquisition, and experiment planning.**
