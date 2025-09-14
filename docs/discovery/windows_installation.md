# Using Dwani.ai on Windows

This guide explains how to download, install, and run the Dwani.ai desktop application on Windows. You can either use the pre-built executable or build the application from source.

## Prerequisites

- **Operating System**: Windows 10 or later (64-bit)
- **Disk Space**: At least 500 MB of free disk space
- **Internet Connection**: Required for downloading the application or dependencies
- **Node.js** (optional, for building from source): Version 16 or higher
- **Git** (optional, for cloning the repository)

## Option 1: Download and Install the Pre-Built Application

1. **Download the Installer**:
   - Visit the [Dwani.ai GitHub Releases](https://github.com/dwani-ai/dwani-desktop/releases/download/v0.0.2/dwani-desktop.Setup.0.0.2.exe) page.
   - Download the Windows executable: `dwani-desktop.Setup.0.0.2.exe`.

2. **Run the Installer**:
   - Locate the downloaded `dwani-desktop.Setup.0.0.2.exe` file in your Downloads folder.
   - Double-click the file to start the installation process.
   - Follow the on-screen prompts to complete the installation.

3. **Launch the Application**:
   - Once installed, find the Dwani.ai application in your Start Menu or on your Desktop (if a shortcut was created).
   - Double-click the Dwani.ai icon to launch the application.

## Option 2: Build and Run from Source

If you prefer to build the application yourself, follow these steps:

### Prerequisites for Building
- Install [Node.js](https://nodejs.org/) (version 16 or higher).
- Install [Git](https://git-scm.com/downloads) to clone the repository.
- Ensure you have `npm` (comes with Node.js) installed.

### Steps to Build

1. **Clone the Repository**:
   Open a terminal (e.g., Command Prompt, PowerShell, or Git Bash) and run:
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
   Build the application for Windows:
   ```bash
   npx electron-builder --win
   ```
   This will generate the Windows executable in the `dist` folder.

4. **Run the Application**:
   - Navigate to the `dist` folder:
     ```bash
     cd dist
     ```
   - Locate the generated `dwani-desktop.Setup.0.0.2.exe` (version may vary).
   - Double-click the `.exe` file to install and run the application, or run it directly from the `dist` folder if an unpacked version is available (e.g., `dwani-desktop.exe`).

## Troubleshooting

- **Installation Fails**: Ensure you have administrative privileges on your Windows account.
- **Application Won’t Start**: Check that your system meets the prerequisites and that the `.exe` file is not blocked by your antivirus software.
- **Build Errors**: Verify that Node.js and npm are correctly installed by running `node -v` and `npm -v` in your terminal.
- For further assistance, visit the [Dwani.ai GitHub Issues](https://github.com/dwani-ai/dwani-desktop/issues) page or contact the support team.

## Additional Notes

- The pre-built executable is recommended for most users as it simplifies the installation process.
- If you encounter issues with the source build, ensure your Node.js and npm versions are compatible.
- Keep your application updated by checking the [GitHub Releases](https://github.com/dwani-ai/dwani-desktop/releases) page for the latest version.