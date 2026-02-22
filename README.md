<p align="center">
  <!-- <a href="https://github.com/Ipotrick/Daxa"> -->
	<img src="misc/daxa-logo.png" width="800" alt="Daxa logo">
  <!-- </a> -->
</p>

# What is this fork?

I needed Daxa to support OpenXR. Almost everything is already there, including access for getting the Vulkan handles for things like the instance, physical device, queue index, etc.
Though for OpenXR image presentation, you need to use a VkImage provided by OpenXR. This branch just adds an extra function to the daxa::Device for creating an image from that external handle.
OpenXR also requires that you ensure the vk instance and device enable a couple extra extensions. That capability is also added in this branch.

I have no idea if anybody else needs Daxa for this, but if you do then let me know and I can work on keeping this branch up-to-date with the main Daxa repository.
If you need to contact me on Discord, you can find me on the Daxa or Graphics Programming discords.

# Why Daxa?
✅ Strong modern GPU focus - no legacy hardware compromises  
🚀 Bindless by default – no descriptor management nor bindings  
🛠️ Shader Build system, shader integration and host/shader code sharing utils  
🧩 Convenient, efficient TaskGraph rendering framework

Daxa is a Vulkan-powered GPU abstraction purpose-built for modern graphics cards (NVIDIA: >=Turing, AMD: >=RDNA3, INTEL: >=Arc). The simplifications and abstractions are done to specifically remove all those api details that no longer matter on modern hardware.

Other than the focus on modern architecture only, what makes Daxa unique?

### Full descriptor/binding abstraction. Full Bindless in shaders and host side.
  * buffers, images, samplers, and acceleration structures are all exclusively accessed via IDs or pointers
  * very efficient on modern hardware
  * dramatically simplifies code as it completely removes one of the largest and headache inducing parts of modern GFX APIs

### Shader Utilities/ Shader Integration.
  * provides full shader build system with #include management, shader hot loading, SPIRV caching and more
  * provides daxa GLSL and SLANG headers allowing for bindless and other daxa feature access in shaders
  * provides daxa.inl file that allows you to write code shareable between host and shader via macros

### TaskGraph acting as full-on rendering framework for your project.
  * automatic synchronization between tasks,  multiple separate TaskGraphs and queues
  * efficient precompilation model: allows you to record graph once and execute it many times, significantly reducing CPU overhead
  * tons of utilities within task callbacks such as linear scratch buffer allocator and automatic image view generation
  * tons of validation checks with detailed error messages explaining the issue and potential solutions
  * automatic graph optimizations: reordering of tasks in order to minimize barriers, memory-aliased transient resources to reduce memory use and more

### Daxa also includes commonly supported Vulkan-middleware features:
* automatic deferring of resource destruction post GPU execution
* internal GPU memory allocator
* default parameters for object construction, simplified object creation
* swapchain synchronization and frame in flight handling
* threadsafety
* access to modern features such as raytracing, mesh shaders and multi queue
* utilitiy classes such as a ringbuffer for staging memory or Dear-ImGui integration

## Getting started

To begin using Daxa, visit [docs.daxa.dev](https://docs.daxa.dev/), where you'll find a comprehensive tutorial and a Wiki containing detailed information about the Daxa API.

* [Daxa Tutorial](https://docs.daxa.dev/tutorial/)
* [Daxa Wiki](https://docs.daxa.dev/wiki/)

Additionally, the Daxa repository includes a collection of example projects located in the **tests** folder.

Working on something with Daxa? Whether it's a renderer, a tool, or just a small experiment—feel free to share it or ask questions on the [Discord server](https://discord.gg/MJPJvZ4FK5). It’s a good place to connect with others using Daxa and stay up to date with ongoing work.
