# ELMA

ELMA (Electrochemistry Lab Multi-frequency Acquisition) drives the lab's hardware setup — Picoscope oscilloscope, TrueForm arbitrary waveform generator, and a BioLogic potentiostat via `pyeclab` — to acquire multi-frequency excitation/response signals from an electrochemical cell in real time, and does the live (online) processing of the streamed data.

Impedance estimation from the acquired (or any other) signals is hardware-agnostic and lives in the separate [`deistools`](https://github.com/federicoscarpioni/DEIStools) package, which ELMA depends on.

## Contents

- `elma.deischannel` — orchestrates a full DEIS measurement channel: potentiostat technique, waveform generator, and oscilloscope acquisition together.
- `elma.picocalculator` — streams data from the Picoscope and drives online block-by-block computation.
- `elma.blockcalculator` — live/online processing of streamed voltage/current blocks (uses `deistools.processing` to estimate impedance per block).
- `elma.multisinegen` — multisine waveform generation/sequencing for the AWG.
- `elma.utils` — shared acquisition helpers (software limit conditions, serialization).

`examples/` contains full measurement scripts showing acquisition + processing wired together against real hardware.

## History note

Split out of [`DEIStools`](https://github.com/federicoscarpioni/DEIStools) `v0.1.0`, which kept acquisition and processing/visualisation in one repo. That combined snapshot remains available at the `DEIStools` repo's `v0.1.0` tag.
