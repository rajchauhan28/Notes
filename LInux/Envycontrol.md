EnvyControl is a lightweight CLI tool for easily switching between integrated, hybrid, and dedicated GPU modes on systems with NVIDIA Optimus technology. It helps manage GPU configurations on Linux, especially for systems that include both an integrated Intel/AMD GPU and a dedicated NVIDIA GPU.

Here are some optimizations and tips for using EnvyControl on Ubuntu:

### 1. **Install EnvyControl**
First, install EnvyControl from its GitHub repository or through `pip`:

```bash
pip install envycontrol
```

Alternatively, you can install it via `git`:

```bash
git clone https://github.com/geminis3/envycontrol.git
cd envycontrol
sudo python3 setup.py install
```

### 2. **Use the Right Mode for Your Needs**
EnvyControl supports three modes: `integrated`, `hybrid`, and `nvidia`. Choose the mode that best fits your use case:

- **Integrated**: Use only the integrated GPU (Intel/AMD). This saves power, reduces heat, and is suitable for everyday tasks like browsing and productivity.
  
  Command:
  ```bash
  sudo envycontrol --switch integrated
  ```

- **Hybrid**: The system will run on the integrated GPU, but you can offload specific applications to the NVIDIA GPU using the `prime-run` command.

  Command:
  ```bash
  sudo envycontrol --switch hybrid
  ```

  For example, to run a game with the NVIDIA GPU in hybrid mode:
  ```bash
  prime-run <application>
  ```

- **NVIDIA**: Use only the dedicated NVIDIA GPU for maximum performance. This is best for gaming or GPU-intensive workloads like AI/ML tasks or video editing.

  Command:
  ```bash
  sudo envycontrol --switch nvidia
  ```

### 3. **Optimizing Power Management**
For better power efficiency, especially in `hybrid` and `integrated` modes, ensure that:

- **TLP** (power management for Linux laptops) is installed and configured:

  ```bash
  sudo apt install tlp
  sudo tlp start
  ```

- **NVIDIA Power Management**:
  Ensure you are using the latest NVIDIA drivers, as they include better power management features. You can install them via `Software & Updates` > `Additional Drivers` or via `apt`:

  ```bash
  sudo apt install nvidia-driver-###  # Replace ### with the recommended driver version
  ```

### 4. **Avoid Screen Tearing**
Screen tearing is common with NVIDIA GPUs. To avoid it, you can configure your system to use a compositor or enable vsync through NVIDIA settings.

1. Open NVIDIA X Server Settings:
   ```bash
   sudo nvidia-settings
   ```

2. In the “X Server Display Configuration” section, click “Advanced”, and enable "Force Composition Pipeline".

3. Apply the settings and save to your X configuration file.

### 5. **Use Vulkan for Better Performance**
For applications that support Vulkan, you can get better performance by using Vulkan over OpenGL. Install Vulkan libraries:

```bash
sudo apt install mesa-vulkan-drivers vulkan-utils
```

Test if Vulkan is working:

```bash
vulkaninfo | less
```

### 6. **Switch Between Modes Without Rebooting**
EnvyControl typically requires a reboot after switching modes, but you can reduce downtime by logging out and logging back in, instead of rebooting.

- To switch to another mode without rebooting, log out (`Ctrl + Alt + Del`) after switching modes, and log back in to apply the changes.

### 7. **Check for Performance Improvements**
For hybrid setups, ensure that applications needing NVIDIA GPU performance are run with `prime-run`. You can verify the active GPU with:

```bash
nvidia-smi
```

This will show the processes using the NVIDIA GPU and help confirm the GPU switch.

### 8. **Monitor GPU Usage**
To track GPU usage, install a tool like `nvtop` for real-time monitoring:

```bash
sudo apt install nvtop
```

Run it:

```bash
nvtop
```

This provides a graphical representation of GPU usage, helping you monitor power consumption and performance.

### 9. **Automate Switching with Scripts**
If you frequently switch between modes (e.g., integrated mode for battery saving, NVIDIA for gaming), you can create scripts to automate the switching process.

Example script to switch to integrated mode:

```bash
#!/bin/bash
sudo envycontrol --switch integrated
```

Make it executable:

```bash
chmod +x switch_to_integrated.sh
```

You can create similar scripts for hybrid and NVIDIA modes.

### 10. **Remove Unnecessary GPU Processes**
Sometimes unnecessary background processes use the GPU, draining power. Use `nvidia-smi` to find and kill them, or disable certain services if they're not needed.

By combining these tips with EnvyControl, you can optimize GPU performance, power consumption, and overall system efficiency on Ubuntu.