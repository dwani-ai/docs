# Using Dwani.ai on Linux

This guide explains how to download, install, and run the Dwani.ai desktop application on Linux. You can either use the pre-built AppImage or build the application from source.

## Prerequisites

- **Operating System**: A 64-bit Linux distribution (e.g., Ubuntu 20.04 or later, Fedora, Debian, etc.)
- **Disk Space**: At least 500 MB of free disk space
- **Internet Connection**: Required for downloading the application or dependencies
- **Node.js** (optional, for building from source): Version 16 or higher
- **Git** (optional, for cloning the repository)

## Option 1: Download and Run the Pre-Built AppImage

1. **Download the AppImage**:
   - Visit the [Dwani.ai GitHub Releases](https://github.com/dwani-ai/dwani-desktop/releases/download/v0.0.2/dwani-desktop-0.0.2.AppImage) page.
   - Download the Linux AppImage: `dwani-desktop-0.0.2.AppImage`.

2. **Make the AppImage Executable**:
   - Open a terminal and navigate to the directory containing the downloaded AppImage (e.g., `~/Downloads`):
     ```bash
     cd ~/Downloads
     chmod +x dwani-desktop-0.0.2.AppImage
     ```

3. **Run the Application**:
   - Execute the AppImage to launch Dwani.ai:
     ```bash
     ./dwani-desktop-0.0.2.AppImage
     ```
   - Alternatively, double-click the AppImage file in your file manager if it supports AppImage execution.

## Option 2: Build and Run from Source

If you prefer to build the application yourself, follow these steps:

### Prerequisites for Building
- Install [Node.js](https://nodejs.org/) (version 16 or higher).
- Install [Git](https://git-scm.com/downloads) to clone the repository.
- Ensure you have `npm` (comes with Node.js) installed.
- Install dependencies for Electron Builder (e.g., `libfuse2` for AppImage support):
  ```bash
  sudo apt-get install libfuse2  # For Debian/Ubuntu-based systems
  sudo dnf install fuse-libs    # For Fedora-based systems
  ```

### Steps to Build

1. **Clone the Repository**:
   Open a terminal and run:
   ```bash
   git clone https://github.com/dwani-ai/dwani-desktop.git
   cd dwani-desktop/frontend
   ```

2. **Install Dependencies**:
   Install the required Node.js packages:
   ```bash
   npm install
   ```

3. **Build the Application**:
   Build the application for Linux:
   ```bash
   npx electron-builder --linux
   ```
   This will generate the Linux AppImage in the `dist` folder.

4. **Run the Application**:
   - Navigate to the `dist` folder:
     ```bash
     cd dist
     ```
   - Make the AppImage executable:
     ```bash
     chmod +x dwani-desktop-0.0.2.AppImage
     ```
   - Run the AppImage:
     ```bash
     ./dwani-desktop-0.0.2.AppImage
     ```

## Troubleshooting

- **AppImage Won’t Run**: Ensure the AppImage is executable (`chmod +x`). If it fails, check for missing dependencies like `libfuse2`.
- **Build Errors**: Verify that Node.js and npm are correctly installed by running `node -v` and `npm -v`. Ensure all build dependencies are installed.
- **Permission Issues**: Run the AppImage or build commands with appropriate permissions (avoid using `sudo` unless necessary).
- For further assistance, visit the [Dwani.ai GitHub Issues](https://github.com/dwani-ai/dwani-desktop/issues) page or contact the support team.

## Additional Notes

- The pre-built AppImage is recommended for most users as it simplifies the installation process.
- AppImages are portable and do not require installation, but you may need to install `libfuse2` on newer Linux distributions.
- Keep your application updated by checking the [GitHub Releases](https://github.com/dwani-ai/dwani-desktop/releases) page for the latest version.

---
