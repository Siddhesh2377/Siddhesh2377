# Siddhesh Sonar
<img src="https://komarev.com/ghpvc/?username=Siddhesh2377&color=0D4715&style=flat" height="25px"/>

**On Device AI + SDK Engineer. I make models run fast on real hardware.**

I work across the full inference stack. Forked llama.cpp, stripped it to CPU only, rewrote the inference paths for Android with big.LITTLE thread scheduling and ARM micro kernels. Built custom Hexagon DSP kernels in HMX/HVX assembly. Currently building cross platform C++ SDK infrastructure at [RunAnywhere](https://runanywhere.ai) (YC W26) with thin native bridges to Kotlin, Swift, Flutter, and React Native.

Not the "import tensorflow and call predict" kind of AI work. The kind where you're writing HMX assembly for a Crouton tile layout and then discovering the matrix unit is fused off on your test silicon.

### What I Built

[**ToolNeuron**](https://github.com/Siddhesh2377/ToolNeuron) Offline AI ecosystem for Android. 400 stars, 47 forks, 5K+ Play Store installs. Three repos: [ToolNeuron](https://github.com/Siddhesh2377/ToolNeuron) (app), [Ai-Systems-New](https://github.com/Siddhesh2377/Ai-Systems-New) (C++ SDK modules), [llama.cpp-android](https://github.com/Siddhesh2377/llama.cpp-android) (custom engine fork). Forked llama.cpp, stripped all GPU backends, built 5 engine layers on top: GGMLEngine, ThreadEngine (big.LITTLE thermal aware scheduling), VLM Engine (20+ vision/audio architectures), RAG Engine (late chunking, binary quantized retrieval), and a callback logger. Four SDK modules: LLM inference, Stable Diffusion (QNN Hexagon DSP + MNN), TTS with 10 voices (ONNX Runtime), emotional TTS with voice cloning (ONNX Runtime). ARM micro kernels: NEON, i8mm, dotprod, fp16, bf16, KleidiAI. ~50 t/s on Cortex X3. No cloud, no telemetry.

**Android NPU** (private). Custom GGUF inference engine that bypasses QNN SDK and dispatches matmul directly to the Hexagon cDSP via FastRPC. Wrote DSP kernel library from scratch in Hexagon assembly: FP16 and INT8 GEMM (HMX), FlashAttention, RMSNorm (HVX), elementwise ops. Weights pre permuted into Crouton tile layout for HMX DMA. Zero copy CPU DSP buffer sharing through rpcmem (ION/dmabuf). Found and fixed 7 FastRPC/DMA/cache pipeline bugs. Diagnosed HMX fuse off on V73 SM7635 through known input verification where the benchmark reported 8 TFLOPS from no op instructions writing zeros. [Blog post](https://siddhesh-blogs.vercel.app/bypassing-qnn-running-llms-on-hexagon-dsp).

**Edge AI Studio** (private). DSL driven inference engine with its own compiler. Write .edge scripts, compile to .egraph binary, run on CPU/CUDA/OpenCL/Qualcomm QNN NPU with per op backend dispatch. Hardware manifests per SoC so the compiler assigns each op to the right backend based on actual device capabilities. Built CLion and VS Code extensions with full LSP (diagnostics, completion, hover, go to definition). Sub 2MB runtime binary. Runs Qwen3 0.6B on Snapdragon. [Blog post](https://siddhesh-blogs.vercel.app/building-a-dsl-for-edge-inference).

[**ForgeAI**](https://github.com/Siddhesh2377/ForgeAi) Desktop app for loading, inspecting, compressing, merging, and testing LLM model files offline. Rust + Tauri v2 + SvelteKit 5. Cross platform.

### What I Actually Understand

**Hardware level inference.** GGML internals and compute graph construction, ML op scheduling across CPU/GPU/NPU, quantization behavior on real silicon (Q4_K_M through Q8_0, IQ variants), how different quant schemes perform on different ARM cores, big.LITTLE thread pinning, thermal zone monitoring.

**Qualcomm Hexagon DSP internals.** HMX matrix extensions (systolic array, Crouton tile layout, accumulator patterns), HVX 1024 bit vector ops (vrmpy, vmpy, vgather), VTCM tightly coupled memory, FastRPC IPC over /dev/cdsprpc, rpcmem zero copy buffer sharing (ION/dmabuf), fastrpc_mmap flags, FARF logging, skel disassembly. Spent weeks debugging at the instruction level on V73.

**Cross platform SDK architecture.** C++ shared core with thin Kotlin/JNI, Swift, Flutter, React Native bridges. V table dispatch for modality routing. Built and maintain this at RunAnywhere.

**Production Android at the metal.** NDK/JNI memory lifecycle, Jetpack Compose, plugin SDK architecture, secure IPC via AIDL, ARM NEON intrinsics (i8mm, dotprod, KleidiAI micro kernels).

### Currently

Building cross platform inference SDK at **RunAnywhere (YC W26)**. Maintain the thin platform bridges over a shared C++ core with V table dispatch. Rewrote the SDK telemetry subsystem from scratch (V table dispatch, per modality event queues, background flush worker). Built a CLI tool for finetuning ML models + LoRAs in C++. Shipped LoRA adapter support across the full stack. 11 PRs across 3 repos, ~16K lines in 6 weeks.

### Contact

[siddheshsonar2377@gmail.com](mailto:siddheshsonar2377@gmail.com) · [LinkedIn](https://www.linkedin.com/in/siddhesh-sonar-7840a7260/) · [Blog](https://siddhesh-blogs.vercel.app)

Open to roles in edge AI, on device inference, mobile SDK infrastructure, and systems programming.
