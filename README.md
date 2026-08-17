# Luna Vision Research

**Research toward reliable real-time assistive computer vision for blind and low-vision users.**

Luna Vision is an ongoing research and engineering project exploring how modern computer vision, spatial computing, localization, OCR, and multimodal systems can support practical environmental understanding and navigation for blind and low-vision users.

The project begins with PC and phone-camera prototypes and is intended to inform future wearable systems.

> **Status:** Active research. This repository documents research findings, experiments, architecture decisions, benchmarks, and reproducibility work. It is not a finished navigation product and should not be treated as a replacement for established mobility aids or professional orientation and mobility training.

## Research Program

Current research areas include:

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

## Research Philosophy

The goal is not simply to make a camera describe an image. A useful assistive vision system needs to maintain useful context over time, understand spatial relationships, distinguish hazards from irrelevant objects, recognize uncertainty, and communicate information without overwhelming the user.

Research in this repository therefore treats Luna Vision as a system-level problem involving perception, localization, memory, reasoning, human-computer interaction, accessibility, and safety.

## Repository Structure

- `research/` - literature reviews, technology landscape work, and source maps
- `findings/` - synthesized conclusions and engineering implications
- `experiments/` - reproducible experiments and prototype investigations
- `benchmarks/` - evaluation methodology and benchmark results
- `architecture/` - proposed system architecture and design decisions
- `reproducibility/` - instructions and records needed to reproduce findings
- `docs/` - supporting public documentation

## Evidence Labels

Material published here should make its evidence level clear:

- **Literature-supported** - conclusion supported by cited external research
- **Reproduced** - result independently reproduced within the Luna research workflow
- **Experimental** - result observed in a Luna experiment but not yet sufficiently validated
- **Hypothesis** - proposed explanation or architecture requiring testing
- **Planned** - intended future investigation or implementation

## Safety and Scope

Assistive navigation is safety-sensitive. Experimental perception output can be incomplete, delayed, or incorrect. Research results in this repository should not be interpreted as proof that a prototype is safe for independent mobility.

Luna Vision is being investigated as an assistive layer, not as justification for removing established mobility tools such as canes, guide dogs, or other appropriate accessibility techniques.

## Public Research Boundary

This repository is intentionally public-facing. It may contain research summaries, citations, architecture diagrams, benchmark methodology, reproducible code, aggregate experimental results, and materials appropriate for a technical portfolio.

Private user data, credentials, private imagery, personally identifying information, proprietary datasets without redistribution rights, and sensitive internal material should not be committed here.

## Current Research Project

### R-004: Luna Vision Assistive Computer Vision Research

R-004 is a broad technical investigation intended to determine what is required to build Luna Vision into a reliable real-time assistive computer-vision system, beginning with PC and phone-camera prototypes and progressing toward wearable hardware.

The investigation covers perception, depth, SLAM, indoor localization, spatial memory, accessible navigation, OCR and product recognition, retail environments, edge inference, reliability, and human-centered evaluation.

Research outputs from R-004 will be progressively published here when they are suitable for public release.

## Long-Term Direction

A mature Luna Vision system would ideally be capable of combining live visual perception with spatial memory and localization to answer practical questions such as:

- What is immediately around me?
- Is there an obstacle or drop-off in my path?
- Where is the doorway, counter, aisle, or destination I need?
- What sign, package, product, or label am I looking at?
- Have I been in this location before?
- Where am I relative to a known indoor map?
- Which route is accessible and appropriate for me?
- How confident is the system in what it is telling me?

Achieving that reliably requires considerably more than object detection alone. This repository documents the research path toward that goal.

## Project Status

**Active research and prototyping, August 2026.**

Expect the repository to evolve as experiments are reproduced, architectures are tested, and findings become strong enough for public documentation.
