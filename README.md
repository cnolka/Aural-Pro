# Aural Pro 🌌

> **"Digital Fireworks for the Cyber Age."**
>
> A real-time, audio-reactive 3D particle system that visualizes sound as flowing digital silk.

![PixPin_2025-12-31_15-53-29](https://github.com/user-attachments/assets/16c1863e-13c7-44d9-a26c-779d52f077d7)

## 📖 About The Project

**Aural Pro** is an experimental digital art project exploring the boundary between chaos and order, sound and light.

It renders **80,000 to 200,000 particles** in real-time, using complex physics simulations driven by music. The project is a testament to human-AI collaboration in 2025:
*   **Creative Direction & Algorithms:** Human
*   **Implementation & Optimization:** Gemini (AI)

Built with pure **WebGL** via **Three.js**, it uses custom **Vertex & Fragment Shaders** to handle massive particle counts while maintaining high frame rates, effectively turning your GPU into a visual synthesizer.

## ✨ Features

*   **Audio Reactivity:** Uses FFT (Fast Fourier Transform) to analyze audio frequencies.
    *   *Bass:* Triggers "Nuclear Boost" expansion waves.
    *   *Treble:* Controls particle jitter and size.
*   **High Performance:** Logic is offloaded to the GPU using custom `ShaderMaterial`.
    *   Real-time **Simplex Noise** calculation in Vertex Shader.
    *   **UnrealBloomPass** for that deep, neon aesthetic on OLED screens.
*   **Dynamic Morphing:** Smoothly transitions between shapes:
    *   Sphere, Tensor Grid, Quantum Lotus, Double Helix, Deep Vortex, and more.
*   **Customizable:** Tweaks for particle count, chaos level, color palettes, and motion speed via Wallpaper Engine properties.

## 🛠️ Technical Highlights

The core magic happens in the GLSL shaders. Instead of updating particle positions on the CPU (which is slow), we pass time and audio data as uniforms to the GPU.

**The "Nuclear Boost" Algorithm:**
A specific ease curve designed to make the bass feel "physical":
```glsl
// Inside Vertex Shader
float safeLow = clamp(uAudioLow, 0.0, 1.0);
// Non-linear expansion based on low frequencies
float expansion = (safeLow * 5.0 + sqrt(safeLow) * 15.0) * uPhysPulse;
vec3 finalPos = pos + noise + (dir * expansion) + jitter;
```

## 🚀 How to Run

### 1. Wallpaper Engine (Recommended)
This project is designed to run natively in **Wallpaper Engine**.
1. Subscribe on Steam Workshop: https://steamcommunity.com/sharedfiles/filedetails/?id=3615005044
2. Select "Aural Pro" in your library.
3. Play some music and enjoy.

### 2. Local Development (Web Browser)
You can run this as a standalone web experiment.
1. Clone the repo:
   ```bash
   git clone https://github.com/your-username/Aural-Pro.git
   ```
2. Install dependencies (if you want to modify imports) or simply run a local server:
   ```bash
   # Using Python
   python -m http.server
   # Or using Node
   npx serve .
   ```
3. Open `localhost:8000` in your browser.
   *Note: Audio reactivity in the browser requires microphone permission or an audio file input implementation (Wallpaper Engine handles system audio injection automatically).*

## ⚙️ Configuration

The project allows extensive customization via `project.json` properties:

| Property | Description |
| :--- | :--- |
| `particle_count` | Adjust from 10k to 200k (GPU dependent). |
| `theme_mode` | Presets like "Deep Sea", "Night City", "Black Gold". |
| `phys_pulse` | Strength of the reaction to bass beats. |
| `light_pulse` | How much the particles flash on sound intensity. |
| `bloom_strength` | Intensity of the glow effect (Post-processing). |

## 🤝 Collaboration Workflow

This project was built using a prompt-engineering workflow:
1. **Ideation:** Defined the visual aesthetic (Cyan/Dark), motion dynamics (Flow/Jitter), and interaction rules.
2. **Code Generation:** Gemini generated the Three.js boilerplate, Shader logic, and optimization strategies.
3. **Refinement:** Iterative tweaking of math functions (easing, noise frequency) to achieve the desired "tingling" sensation.

## 📄 License

Distributed under the MIT License. See `LICENSE` for more information.

---
*Created on the eve of 2026.*
