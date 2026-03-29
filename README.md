# Siddhesh Sonar
<img src="https://komarev.com/ghpvc/?username=Siddhesh2377&color=0D4715&style=flat" height="25px"/>

**On Device AI Engineer. I make models run fast on phones.**

I work across the full inference stack. Tensor level optimizations in GGML and C++, JNI bindings, Qualcomm NPU dispatch, all the way up to production Android apps. Currently building on device inference infrastructure at [RunAnywhere](https://runanywhere.ai) (YC W26).

I spend most of my time inside GGML compute graphs, Qualcomm QNN internals (Hexagon DSP, HVX, VTCM), and llama.cpp source code. Not the "import tensorflow and call predict" kind of AI work. The kind where you're staring at memory bandwidth bottlenecks on a Snapdragon 8 Gen 3 and figuring out why your NPU graph is 2x slower than it should be.

### What I Built

[**ToolNeuron**](https://github.com/Siddhesh2377/ToolNeuron) 309 stars, 2.9K+ installs. Complete offline AI ecosystem for Android. Runs LLMs, vision models, Stable Diffusion, TTS, and RAG entirely on device. No cloud, no telemetry. 600+ commits. Custom JNI bindings to llama.cpp with ARM optimizations (NEON, KleidiAI micro kernels, CPU affinity pinning). Plugin SDK with sandboxed extensions and hardware backed AES 256 GCM encryption. Real users include a military psychology researcher from the Netherlands.

[**Ai Core**](https://github.com/Siddhesh2377/Ai-Core) 29 stars. Native C/C++ inference engine that powers ToolNeuron. Direct GGML integration, custom tensor ops optimized for mobile SOCs. Benchmarks at ~30 t/s on Cortex X3 with a 350M parameter model.

**Edge AI Studio** (private). DSL driven inference engine with its own compiler. Write .edge scripts, compile to .egraph binary, run on CPU/CUDA/OpenCL/Qualcomm QNN NPU with per op backend dispatch. Built CLion and VS Code extensions with full LSP. Sub 2MB runtime binary. Runs Qwen3 0.6B on Snapdragon today.

[**ForgeAI**](https://forge-64364c0e.mintlify.app/getting-started/introduction) Toolkit for SafeTensors and GGUF model operations. Inspection, conversion, manipulation.

### What I Actually Understand (Not Buzzwords)

**Hardware level inference.** GGML internals and compute graph construction, ML op scheduling across CPU/GPU/NPU, quantization behavior on real silicon (Q4_K_M, Q5_K_S, Q8_0), how different quant schemes actually perform on different ARM cores.

**Qualcomm SOC architecture.** Hexagon DSP with HVX vector extensions and HMX matrix extensions, VTCM tightly coupled memory, Adreno GPU compute pipelines, QNN SDK for NPU graph compilation and dispatch, the real constraints around NPU memory bandwidth and operator coverage.

**Production Android at the metal.** NDK/JNI memory lifecycle, Jetpack Compose, plugin SDK architecture, secure IPC via AIDL, AOSP level optimizations, ARM NEON intrinsics.

### Currently

Building cross platform inference SDK at **RunAnywhere (YC W26)** across C++, Kotlin, and JNI. Shipped LoRA adapter support end to end, fixed Gradle build systems, wrote SDK docs with 18 custom diagrams. 11 PRs across 3 repos in 6 weeks.

Also deepening formal math (linear algebra, quantization theory via 3Blue1Brown approach) to complement the hands on systems work.

### Contact

[siddheshsonar2377@gmail.com](mailto:siddheshsonar2377@gmail.com) · [LinkedIn](https://www.linkedin.com/in/siddhesh-sonar-7840a7260/) · [Blog](https://siddhesh-blogs.vercel.app) · [X](https://x.com/Sonar_2377)

Open to full time roles in edge AI, on device inference optimization, and mobile AI infrastructure.
