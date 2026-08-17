# Research Methodology

Luna Vision uses a staged evidence workflow intended to separate interesting ideas from reproduced engineering evidence.

## 1. Start from a concrete system question

Examples:

- Can a phone camera and IMU maintain reliable pose through a normal indoor route?
- Is monocular depth stable enough to detect specific household hazards?
- Can a known floor plan help Luna recover after localization loss?
- How should stale object information be represented in persistent spatial memory?

A research run should be attached to a question that can change a design decision.

## 2. Review primary technical evidence

Preference is given to:

- peer-reviewed papers
- official repositories
- official dataset documentation
- official product and platform documentation
- accessibility research involving blind and low-vision users
- benchmark publications and reproducible methods

Secondary summaries can help discover work, but important technical claims should be traced back to primary evidence.

## 3. Separate source evidence from Luna conclusions

The workflow distinguishes:

- what an upstream paper or project reports
- what Luna has independently reproduced
- what was observed in a Luna-specific experiment
- what remains an engineering hypothesis

This prevents a published benchmark result from being accidentally represented as Luna's own performance.

## 4. Preserve reproducibility information

For experiments, record as much of the following as practical:

- hardware
- operating system and environment
- software and model versions
- datasets and exact subsets
- calibration
- test procedure
- metrics
- latency and resource usage
- failure cases
- deviations from upstream instructions
- date and experiment identifier

## 5. Test failure conditions deliberately

Assistive computer vision should not be evaluated only on attractive demo scenes.

Important stress conditions include:

- low light
- motion blur
- blank or low-texture walls
- mirrors and reflective surfaces
- glass and transparent objects
- thin obstacles
- low obstacles and overhanging obstacles
- moving people
- repeated or ambiguous rooms
- moved furniture
- dropped frames
- sensor interruption
- localization loss
- map staleness
- model disagreement

## 6. Use system-level metrics

A model can score well on a conventional benchmark while still being unsuitable for an assistive workflow.

Luna therefore tracks conventional model metrics alongside system measures such as:

- end-to-end latency
- false-negative hazard rate
- false-stop rate
- tracking uptime
- re-localization success and recovery time
- temporal stability
- confidence calibration
- map freshness
- dropped frames
- compute and memory use
- graceful degradation behavior

## 7. Require stage-appropriate safety boundaries

Early prototypes are research instruments, not mobility products.

Recorded replay, simulation, tabletop testing, supervised indoor testing, and real-user trials are different evidence stages. A result should not be promoted to a higher safety claim merely because a demonstration looked successful.

## 8. Publish useful negative results

Failed reproduction attempts, unstable models, unexpected latency, calibration problems, and failure cases are useful research outputs when documented clearly.

The public repository aims to show the reasoning path, not only successes.

## 9. Maintain a public/private boundary

The private research workspace can contain raw notes, source copies, internal planning, private recordings, and material that requires review.

This public repository receives only material that is appropriate to release under the repository's publication policy.

## 10. Update conclusions when evidence changes

Architecture decisions in Luna Vision are working hypotheses. Reproduced evidence should be allowed to overturn earlier assumptions.

The goal is a system whose design becomes more evidence-based over time rather than one built to defend its first architecture.
