# PNAM — Parametric Neural Amp Modeler

**PNAM (Parametric Neural Amp Modeler)** is an experimental extension of the [Neural Amp Modeler (NAM)](https://github.com/sdatkinson/NeuralAmpModelerCore) ecosystem, built upon [phillipmself's Parametric Neural Amp Modeler fork](https://github.com/phillipmself/neural-amp-modeler-parametric).

The project aims to expand neural audio modeling beyond static captures by introducing **parameterized neural models** capable of representing individual pieces of audio equipment and their interactive controls.

Rather than capturing an entire amplifier or effects chain as a fixed configuration, PNAM aims to model the behavior of individual controls and their interactions, allowing users to adjust modeled equipment parameters after training.

The long-term goal is to establish an integrated ecosystem for parametric modeling, dataset capture, model training, and real-time audio playback.

---

## Project Vision

Traditional Neural Amp Modeler captures the behavior of a complete signal chain under a particular configuration. While this approach produces highly realistic results, changing the original equipment's settings generally requires another capture and model.

PNAM explores a different approach: **modeling the equipment itself as a controllable system.**

A single parametric model could potentially represent multiple configurations of the same equipment through exposed controls such as gain, tone, volume, and pickup selection.

The project is built around the following objectives:

- **Parametric Modeling:** Learn equipment characteristics and expose their controls as adjustable parameters.
- **Control Interaction Modeling:** Capture nonlinear relationships and dependencies between multiple controls.
- **Flexible Architectures:** Explore neural architectures specifically designed for parameterized audio systems.
- **Integrated Workflow:** Simplify the process of equipment capture, dataset preparation, and model training.
- **Unified Playback:** Provide a dedicated plugin capable of loading and playing both conventional and parametric NAM models.

## Planned Features & Development Roadmap

### 1. FP-WaveNet Modeling Architecture
<sub>Development status: In Progress</sub>

**FP-WaveNet (Factorized Parametric WaveNet)** is an interaction-aware neural architecture designed for parametric equipment modeling.

Its approach is to learn individual control characteristics and their nonlinear dependencies before integrating them into a unified audio-processing network.

The architecture aims to:

- Learn the individual influence of each equipment parameter.
- Capture nonlinear interactions between multiple parameters.
- Represent parameter-dependent changes in the audio signal.
- Support a modular and factorized modeling approach.
- Combine learned parameter representations into a unified audio-processing architecture.

The goal is to create models that respond naturally to parameter changes, rather than simply interpolating between independently captured configurations.

### 2. Multi-Position Switch Parameters
<sub>Development status: Planned</sub>

The existing parametric training workflow primarily focuses on continuous, ranged parameters.

PNAM aims to introduce support for **discrete multi-position switches**, allowing models to represent equipment controls that have a finite number of selectable states.

Examples include:

- Amplifier voicing switches.
- Bright switches.
- Channel selectors.
- Other discrete equipment controls.

This will allow PNAM to represent a broader range of real-world equipment configurations beyond conventional rotary knobs and sliders.

### 3. Enhanced PNAM Capture & Trainer Software
<sub>Development status: Planned</sub>

An integrated capture and training application is planned to simplify the entire parametric modeling workflow.

The software will aim to provide a user-friendly environment for capturing equipment responses, organizing datasets, configuring models, and starting training sessions.

Planned capabilities include:

- Guided equipment capture workflows.
- Automated dataset organization and preparation.
- Parametric control configuration.
- Model architecture and training configuration.
- Training progress monitoring.
- Compatibility with existing NAM workflows where practical.
- Support for FP-WaveNet and ConcatWaveNet training architectures.

**Usability and compatibility** will be key priorities, making advanced parametric modeling more accessible without requiring users to manage every stage manually.

### 4. Dedicated `.pnam` File Format
<sub>Development status: Proposed</sub>

PNAM proposes introducing a dedicated `.pnam` file extension for parameterized models.

The distinction is intended to make the two modeling approaches easier to identify:

| Extension | Model Type | Intended Purpose |
|---|---|---|
| `.nam` | Conventional NAM model | Captures a fixed equipment or signal-chain configuration. |
| `.pnam` | Parametric NAM model | Represents equipment with configurable parameters and control interactions. |

A `.nam` model represents a particular captured configuration, whereas a `.pnam` model is intended to represent a configurable piece of equipment.

The proposed extension will also help applications identify which playback interface and parameter controls are required.

Compatibility with existing NAM tooling and model conventions will be considered during implementation.

### 5. PNAM Plugin
<sub>Development status: Planned</sub>

A dedicated PNAM plugin is planned to serve as a unified playback environment for conventional `.nam` and parametric `.pnam` models.

The plugin will automatically adapt its interface depending on the loaded model type.

**For `.nam` models:**
- Conventional NAM playback.
- Standard model loading and management.
- No additional parameter controls unless supported by the model.

**For `.pnam` models:**
- Parametric model playback.
- Dynamically generated control interfaces.
- Adjustable knobs, sliders, and multi-position switches.
- Parameter configurations defined by the model.

The goal is to provide a seamless experience where users can load either model type without needing separate plugins.

---

## Long-Term Goals

PNAM aims to develop into a complete parametric neural modeling ecosystem consisting of three interconnected components:

1. **Capture:** Tools for systematically capturing equipment responses across different parameter configurations.
2. **Training:** Neural architectures and training software capable of learning equipment behavior and control interactions.
3. **Playback:** A dedicated plugin for loading, controlling, and playing trained models in real time.

Ultimately, PNAM aims to make neural modeling more flexible by moving from capturing individual equipment configurations toward capturing the behavior of the equipment itself.

## Project Status

PNAM is currently under active development. Its architecture, tooling, file format, and plugin workflow are subject to change.

The features described in this README represent development goals and proposals; they should not be interpreted as features that are already implemented.

## Acknowledgements

PNAM builds upon the work of the Neural Amp Modeler community, particularly:

- [Neural Amp Modeler](https://github.com/sdatkinson/NeuralAmpModelerCore) — The original neural audio modeling ecosystem.
- [phillipmself/neural-amp-modeler-parametric](https://github.com/phillipmself/neural-amp-modeler-parametric) — The parametric NAM fork that serves as the foundation for this project.

Thanks to the developers and contributors whose work makes projects like PNAM possible.

---

*PNAM — Moving from modeling equipment configurations to modeling the equipment itself.*
