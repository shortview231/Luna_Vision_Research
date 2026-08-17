# High-Value Source Map

**Research program:** R-004 Luna Vision Assistive Computer Vision Research  
**Date:** 2026-08-16  
**Purpose:** Public index of especially relevant sources identified during the initial Luna Vision research landscape.

This file is not a claim that every source has been reproduced or adopted. It maps research questions to primary projects, datasets, and reference systems that appear especially useful for Luna Vision.

## Accessibility and Egocentric Vision

### SANPO

- Project: https://google-research-datasets.github.io/sanpo_dataset/
- Focus: first-person navigation-scene understanding, stereo video, depth, and panoptic labels
- Luna use: perception benchmarking for navigation-relevant scenes
- Status: dataset access and practical download footprint still require verification before broad use

### EgoBlind

- Project: https://github.com/doc-doc/EgoBlind
- Focus: real questions and intentions expressed by blind users from egocentric video
- Luna use: conversational visual-assistance and user-intent evaluation
- Status: high-priority evaluation resource

### GuideDog

- Paper: https://aclanthology.org/2026.acl-long.251/
- Focus: accessibility-aware pedestrian-scene descriptions and question answering
- Luna use: descriptive guidance and depth-reasoning evaluation
- Initial implication: current multimodal systems should not be treated as the sole geometry or safety layer

### Project Guideline

- Project: https://sites.research.google/guideline/
- Focus: real-time outdoor navigation assistance using mobile computer vision and accessible audio feedback
- Luna use: important precedent for phone-first sensing, stateful perception, route guidance, and feedback design

## Depth and Geometry

### Depth Anything V2

- Repository: https://github.com/DepthAnything/Depth-Anything-V2
- Focus: monocular depth estimation
- Luna use: practical depth baseline for the PC/phone prototype
- Research question: how stable is monocular depth across indoor hazard classes, materials, motion, lighting, and distance?

### Dedicated depth sensing

- Reference class: phone LiDAR and RGB-D cameras
- Focus: direct metric geometry
- Luna use: comparator for monocular depth
- Research question: does the improvement in hazard detection justify additional power, hardware, placement, and cost?

## Localization, SLAM, and Mapping

### ORB-SLAM3

- Repository: https://github.com/UZ-SLAMLab/ORB_SLAM3
- Focus: visual and visual-inertial SLAM, mapping, loop closure, and re-localization
- Luna use: primary SLAM baseline
- Important limitation: real-world robustness must be tested under feature-poor surfaces, motion blur, lighting changes, and moving scenes

### OpenVINS

- Documentation: https://docs.openvins.com/
- Repository: https://github.com/rpng/open_vins
- Focus: filter-based visual-inertial navigation
- Luna use: lightweight complementary baseline with explicit covariance and uncertainty information

### RTAB-Map

- Repository: https://github.com/introlab/rtabmap
- Focus: long-term appearance-based mapping, loop closure, occupancy and 3D mapping
- Luna use: persistent spatial-memory and map experiments

### PALMS / PALMS+

- Repository: https://github.com/Head-inthe-Cloud/PALMS-Plane-based-Accessible-Indoor-Localization-Using-Mobile-Smartphones
- Focus: infrastructure-free localization against an existing floor plan
- Luna use: high-priority reproduction target for persistent indoor localization and re-localization

### TUM Visual-Inertial Dataset

- Dataset: https://cvg.cit.tum.de/data/datasets/visual-inertial-dataset
- Focus: synchronized stereo cameras, IMU, and ground-truth motion
- Luna use: standardized localization benchmark before home navigation experiments

### EuRoC MAV Dataset

- Dataset: https://projects.asl.ethz.ch/datasets/euroc-mav/
- Focus: stereo visual-inertial benchmark sequences
- Luna use: second baseline to reduce overfitting to one localization benchmark

## Spatial Memory and Simulation

### Habitat / HM3DSem

- Platform: https://aihabitat.org/
- Semantic dataset: https://aihabitat.org/datasets/hm3d-semantics/
- Focus: embodied-agent simulation and semantic indoor environments
- Luna use: repeatable testing of route logic, room/object memory, and failure handling before controlled human trials

### NVIDIA Isaac Sim

- Platform: https://developer.nvidia.com/isaac/sim
- Focus: robotics simulation and synthetic sensor/data generation
- Luna use: later-stage controlled generation of difficult obstacles, sensor failures, shelf layouts, and hardware-oriented scenarios

## Retail and Product Interaction

### SKU-110K

- Paper: https://openaccess.thecvf.com/content_CVPR_2019/html/Goldman_Precise_Detection_in_Densely_Packed_Scenes_CVPR_2019_paper.html
- Focus: dense product-instance detection on retail shelves
- Luna use: shelf-instance detection before exact product identity

### Seeing AI

- Product: https://www.microsoft.com/en-us/ai/seeing-ai
- Focus: specialized visual-assistance modes including text and product/barcode interaction
- Luna use: mature product precedent for task-specific accessible interaction

### Apple Magnifier Detection Mode

- Documentation: https://support.apple.com/guide/iphone/use-detection-mode-iph70f7f0c9c/ios
- Focus: people, doors, furniture, text, scenes, LiDAR-assisted detection, speech, sound, haptics, and visual feedback
- Luna use: multimodal feedback and direct-depth precedent

## Edge and Wearable Compute

### NVIDIA Jetson Orin Nano

- Documentation: https://developer.nvidia.com/embedded/learn/jetson-orin-nano-devkit-user-guide/index.html
- Focus: portable edge inference
- Luna use: later-stage portable compute benchmark after desktop requirements are measured
- Initial design implication: pocket, belt, or backpack compute may be more practical before electronics are integrated directly into a hat

## How This Map Should Evolve

Each source should eventually be assigned one or more of these statuses:

- `REFERENCE_ONLY`
- `ACCESS_VERIFIED`
- `DATA_ACQUIRED`
- `REPRODUCTION_QUEUED`
- `REPRODUCED`
- `BENCHMARKED_IN_LUNA`
- `REJECTED_FOR_LUNA`
- `DEFERRED`

The long-term goal is to turn this from a reading list into a reproducibility and evidence map showing what Luna has actually tested.
