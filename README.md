# OmniDirection
### Binaural Spatial Audio Engine

A Python-based digital signal processing (DSP) prototype that turns stereo audio into immersive 3D spatial audio for headphones without external spatial audio frameworks.

## Core DSP Features

* **Equal-Power Panning (ILD):** Uses a sine/cosine law ($\cos^2\theta + \sin^2\theta = 1$) to prevent volume drops during rotation.
* **Interaural Time Difference (ITD):** Implements dynamic sub-millisecond sample shifts ($\le0.7\text{ms}$) to simulate sound arrival lag between ears.
* **Distance Occlusion Filtering:** Applies a 2nd-order Butterworth low-pass filter ($4000\text{ Hz}$ cutoff) to model head shadowing and acoustic absorption.
* **Multi-Tap Early Reflections:** Uses cross-channel delay lines ($12\text{ms}$, $24\text{ms}$, $38\text{ms}$) with exponential decay to create realistic room depth.
* **Peak Normalization:** Prevents 16-bit PCM integer overflow and clipping distortion.

---

## Technical Pipeline

[Stereo Input] ──► [Equal-Power Panning] ──► [ITD Sample Shift] <br>
│ <br>
▼ <br>
[16-bit WAV Export] ◄── [Peak Normalization] ◄── [Multi-Tap Reverb + LPF]
