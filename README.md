# CPU INFOrmation library

cpuinfo is a library to detect essential for performance optimization information about host CPU.

Exposed information:
- [ ] Processor (SoC) name
- [x] Microarchitecture
- [x] Usable instruction sets
- [x] Cache
  - [x] Size
  - [x] Associativity
  - [x] Line size
  - [x] Number of partitions
  - [x] Flags (unified, inclusive, complex hash function)
  - [x] Topology (logical processors that share this cache level)
- [ ] TLB
  - [ ] Number of entries
  - [ ] Associativity
  - [ ] Covered page types (instruction, data)
  - [ ] Covered page sizes
- [ ] Topology information
  - [ ] Logical processors
  - [ ] Cores
  - [ ] Packages (sockets)

Supported environments:
- [x] Linux
  - [x] x86
  - [x] x86-64
  - [x] 32-bit ARM (ARMv5T and later)
  - [ ] ARM64
  - [ ] PowerPC
- [x] OS X
  - [x] x86
  - [x] x86-64
- [ ] Windows
  - [ ] x86
  - [ ] x86-64
- [x] Android
  - [x] x86 ABI
  - [x] x86_64 ABI
  - [x] armeabi ABI
  - [x] armeabiv7-a ABI
  - [ ] arm64-v8a ABI
  - [ ] mips ABI
  - [ ] mips64 ABI
- [ ] Native Client
  - [ ] x86
  - [x] x86-64
  - [ ] ARMv7-A
- [ ] Portable Native Client
- [ ] Emscripten

Planned features:

- Processor (SoC) name detection
  - [ ] Using CPUID leaves 0x80000002–0x80000004 on x86/x86-64
  - [ ] Using `/proc/cpuinfo` on ARM
  - [ ] Using kernel log (`dmesg`) on ARM
  - [ ] Using `ro.chipname`, `ro.board.platform`, `ro.product.board` properties (Android)
- Vendor and microarchitecture detection
  - [x] Intel-designed x86/x86-64 cores (up to Kaby Lake, Airmont, and Knights Mill)
  - [x] AMD-designed x86/x86-64 cores (up to Puma/Jaguar and Zen)
  - [ ] VIA-designed x86/x86-64 cores
  - [ ] Other x86 cores (DM&P, RDC, Transmeta, Cyrix, Rise)
  - [x] ARM-designed ARM cores (up to Cortex-A17, Cortex-73)
  - [x] Qualcomm-designed ARM cores (up to Kryo and Kryo-280)
  - [x] nVidia-designed ARM cores (Denver)
  - [x] Samsung-designed ARM cores (Mongoose)
  - [x] Intel-designed ARM cores (XScale up to 3rd-gen)
  - [ ] Apple-designed ARM cores (up to Hurricane)
  - [ ] Server ARM cores
- Instruction set detection
  - [x] Using CPUID on x86/x86-64 (Linux, Mach)
  - [x] Using dynamic code generation validator on x86-64 (Native Client)
  - [x] Using `/proc/cpuinfo` on 32-bit ARM EABI (Linux)
  - [x] Using microarchitecture heuristics on 32-bit ARM
  - [x] Using `FPSID` and `WCID` registers on 32-bit ARM
  - [ ] Using `getauxval` or `/proc/self/auxv` (Linux)
  - [ ] Using instruction probing on ARM (Linux)
- Cache detection
  - [x] Using CPUID leaf 0x00000002 on x86/x86-64
  - [x] Using CPUID leaf 0x00000004 on non-AMD x86/x86-64
  - [ ] Using CPUID leaves 0x80000005-0x80000006 on AMD x86/x86-64
  - [x] Using CPUID leaf 0x8000001D on AMD x86/x86-64
  - [x] Using `/proc/cpuinfo` on ARMv6 and earlier (Linux)
  - [x] Using microarchitecture heuristics on 32-bit ARM
  - [x] Using `sysctlbyname` (Mach)
  - [ ] Using sysfs (Linux)
  - [ ] Using `clGetDeviceInfo` with `CL_DEVICE_GLOBAL_MEM_CACHE_SIZE`/`CL_DEVICE_GLOBAL_MEM_CACHELINE_SIZE` parameters (Android)
- TLB detection
  - [x] Using CPUID leaf 0x00000002 on x86/x86-64
  - [ ] Using CPUID leaves 0x80000005-0x80000006 and 0x80000019 on AMD x86/x86-64
  - [x] Using microarchitecture heuristics on 32-bit ARM
- Topology detection
  - [x] Using CPUID leaf 0x00000001 on x86/x86-64 (legacy APIC ID)
  - [x] Using CPUID leaf 0x0000000B on x86/x86-64 (Intel APIC ID)
  - [ ] Using CPUID leaf 0x8000001E on x86/x86-64 (AMD APIC ID)
  - [x] Using `host_info` (Mach)
  - [ ] Using sysfs (Linux)
