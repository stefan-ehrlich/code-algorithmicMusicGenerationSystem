## Overview

This repository contains the **rule-based probabilistic algorithmic music generation system** presented in:

> Ehrlich, S. K., Agres, K. R., Guan, C., & Cheng, G. (2019).  
> *A closed-loop, music-based brain-computer interface for emotion mediation.*  
> PLOS ONE, 14(3), e0213516. https://doi.org/10.1371/journal.pone.0213516 

The system generates **continuous, controllable affective music** in real time. Its key property is that it allows **smooth transitions** between affective expressions (e.g., *happy → sad → angry*) by continuously varying two control parameters:

- **val** ∈ [0, 1]  (valence)
- **aro** ∈ [0, 1]  (arousal)

These affect parameters are mapped to musically meaningful structural parameters, enabling music generation along arbitrary trajectories through **valence–arousal affective space** (Russell/Thayer style).

---

## Algorithm in brief

### Core concept
The algorithm is implemented as a **rule-based probabilistic state machine** that generates streams of **MIDI events** (notes/chords). The probability of note events and their attributes is continuously modulated by the affect controls `(val, aro)`.

### Mapping emotion → musical structure
Following established psychological findings on music emotion, the system maps **valence/arousal** onto five structural music parameters.

1. **Tempo** (linked to arousal)
2. **Rhythmic roughness / density** (linked to arousal; more notes = higher complexity/activation)
3. **Relative loudness of subsequent tones** (linked to arousal)
4. **Pitch register (overall pitch)** (linked to valence)
5. **Harmonic mode** (linked to valence; discrete 7-step diatonic modes (Lydian → … → Locrian) ordering)

### Musical style / rendering
The generator outputs MIDI and was used in the study with three virtual instruments:
- piano
- cello
- bass

resulting in a **small classical chamber-orchestra style**. :contentReference[oaicite:6]{index=6}

---

## Repository structure

```text
code-algorithmicMusicGenerationSystem/
├── composer_algorithm.m            # main probabilistic MIDI generator + affect mapping (val/aro → structure)
├── trajectory_gen.m                # generate trajectories through affective space (valence/arousal over time)
├── trj_*.mat                       # example affective trajectories (valence/arousal)
├── sound_examples/                 # rendered audio examples of generated music
├── russel.png                      # affective space illustration (valence/arousal plane)
├── LICENSE
└── README.md
```

## Citation
If you use this code in research, please cite:

@article{ehrlich2019closedloop,
  title   = {A closed-loop, music-based brain-computer interface for emotion mediation},
  author  = {Ehrlich, Stefan K. and Agres, Kat R. and Guan, Cuntai and Cheng, Gernot},
  journal = {PLOS ONE},
  volume  = {14},
  number  = {3},
  pages   = {e0213516},
  year    = {2019},
  doi     = {10.1371/journal.pone.0213516}
}


