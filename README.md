# Orange OS

**Orange OS** is a simple, yet cool operating system designed with minimalism and functionality in mind. Perfect for educational purposes, hobbyists, or those looking to dip their toes into OS development.

---

## Features

- Lightweight and efficient OS
- Built using Rust, leveraging key low-level system libraries
- Provides a solid base for learning OS internals like memory management, hardware interaction, and multitasking
- Runs on x86 compatible hardware/emulators

---

## Getting Started

Follow the instructions below to set up, build, and run Orange OS.

### Requirements

1. **Rust Nightly**  
   Install the nightly version of Rust as it's required for low-level OS development. Run:
   ```bash
   rustup install nightly
   rustup default nightly
   ```

2. **Additional Tools**
    - `bootimage` for building bootable images of the OS:
      ```bash
      cargo install bootimage --version "^0.9.0"
      ```
    - `qemu` for emulating Orange OS:
      ```bash
      # For MacOS:
      brew install qemu
      # For other platforms, refer to https://www.qemu.org/download/
      ```

3. **Cargo Dependencies**  
   Key libraries used:
    - `spin`, a lock-free synchronization library
    - `uart_16550`, for serial port communication
    - `x86_64`, utilities for creating x86-64 based systems
    - `bootloader`, for linking minimal boot code to your kernel

   `Cargo` will automatically ensure these dependencies are installed during the build process.

---

### Building the OS

1. Clone the repository:
   ```bash
   git clone https://github.com/CyberRubberDucky/orangeosbevy.git
   cd orange-os
   ```

2. Build the OS. The `bootimage` tool will assemble a bootable binary:
   ```bash
   cargo bootimage
   ```

---

### Running the OS

After building, test the OS in an emulator or real hardware.

#### Run in QEMU
Launch Orange OS in the QEMU emulator:
```bash
qemu-system-x86_64 -drive format=raw,file=target/x86_64-unknown-none/debug/bootimage-orange-os.bin
```

#### Run on Real Hardware
1. Flash the `.bin` file to a USB drive:
   ```bash
   sudo dd if=target/x86_64-unknown-none/debug/bootimage-orange-os.bin of=/dev/sdX bs=4M
   ```
   Replace `/dev/sdX` with the appropriate drive identifier.

2. Boot the system from the USB drive on your hardware.

---

## Code Overview

- **Kernel**: Core logic that interacts with hardware
- **Memory Management**: Handles allocation and deallocation dynamically
- **Interrupts**: Implements various handlers for hardware/software
- **Drivers**: Basic drivers, e.g., keyboard, serial communications
- **Scheduler** (Optional): If implemented, for multitasking

Feel free to explore the codebase to understand each component.

---

## Contributing

Orange OS is a personal project but contributions/feedback are always welcome! Feel free to fork and submit a pull request or log issues.

---

## Acknowledgments

This project is built using lessons and tools from the wonderful Rust and OS development communities. Huge thanks to open-source contributors who provided libraries and examples!

---

## Disclaimer

Orange OS is purely for educational purposes and not meant for production use.

---

Enjoy and have fun exploring **Orange OS**!
