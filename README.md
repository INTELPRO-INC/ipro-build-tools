# IPRO Build Tools

The host build tools for the IPRO SDK: CMake, a build program and Python.

| System | How to get them |
|---|---|
| Windows x64 | [`IPRO-build-tools-windows-2026.09.09.zip`](https://github.com/INTELPRO-INC/ipro-build-tools/releases/download/v2026.09.09/IPRO-build-tools-windows-2026.09.09.zip) (53 MB): CMake 3.30.5, Ninja 1.12.1, Python 3.12.7 with pyserial 3.5 |
| macOS | Homebrew and the Xcode command-line tools (below) |
| Linux | the system package manager (below) |

The SDK needs CMake 3.15 or later (3.20 or later for Zephyr), GNU make or Ninja, and Python 3.8 or later with pyserial for the serial console.

## Windows

[IPRO SDK Online Setup](https://github.com/INTELPRO-INC/ipro-sdk-releases) installs this package for you; the VS Code Extension and `build_freertos.ps1` then find the tools. To install it by hand:

1. Download [`IPRO-build-tools-windows-2026.09.09.zip`](https://github.com/INTELPRO-INC/ipro-build-tools/releases/download/v2026.09.09/IPRO-build-tools-windows-2026.09.09.zip) (53 MB).
2. In PowerShell, in the download folder, check the file:

   ```powershell
   (Get-FileHash .\IPRO-build-tools-windows-2026.09.09.zip -Algorithm SHA256).Hash
   ```

   You should see `634962548EFFA5700B87BB0DA898C8F3DC5524E99B871A330ABDDCD179A5B4EE`.
3. Extract it to `C:\IPRO`:

   ```powershell
   Expand-Archive .\IPRO-build-tools-windows-2026.09.09.zip -DestinationPath C:\IPRO
   ```

4. Check it:

   ```powershell
   C:\IPRO\tools\cmake\bin\cmake.exe --version
   C:\IPRO\tools\ninja\ninja.exe --version
   C:\IPRO\tools\python\python.exe -m serial.tools.list_ports -h
   ```

   `cmake.exe` prints `cmake version 3.30.5`.
   `ninja.exe` prints `1.12.1`.
   `python.exe` prints the help of pyserial's port lister.

After a manual install, add `C:\IPRO\tools\cmake\bin`, `C:\IPRO\tools\ninja` and `C:\IPRO\tools\python` to `PATH`.

## macOS

```bash
brew install cmake python3
xcode-select --install          # GNU make
python3 -m pip install --user pyserial
cmake --version                 # cmake version 3.15 or later
```

## Linux (Ubuntu / Debian)

```bash
sudo apt install cmake make python3 python3-serial
cmake --version                 # cmake version 3.15 or later
```

On Linux x86-64 the SDK build falls back to the CMake 3.15 in its `tools/cmake/` when no `cmake` is on `PATH`.

## Where the packages are published

Each version is a release of this repository with the packages and `SHA256SUMS.txt`.
The Windows package is also kept, byte for byte, in the IPRO-SDK release [components-2026.09.09](https://github.com/INTELPRO-INC/IPRO-SDK/releases/tag/components-2026.09.09): the current versions of [IPRO SDK Online Setup](https://github.com/INTELPRO-INC/ipro-sdk-releases) download it from there, so that release stays unchanged.

## License

CMake (BSD 3-Clause), Ninja (Apache 2.0), Python (PSF License) and pyserial (BSD 3-Clause); the license texts are inside the package.

## 繁體中文

這個 repo 發佈建置工具，Windows 提供 CMake／Ninja／Python 套件，macOS 與 Linux 用系統套件管理器安裝。Windows 一般用 [IPRO SDK Online Setup](https://github.com/INTELPRO-INC/ipro-sdk-releases) 安裝即可。手動安裝時照上面各系統的步驟：下載、核對 SHA-256、解壓到 `C:\IPRO`，再執行檢查指令。完整說明見[文件站](https://intelpro-inc.github.io/ipro-sdk-docs/)。

## Related

[IPRO SDK](https://github.com/INTELPRO-INC/IPRO-SDK) · [Online Setup](https://github.com/INTELPRO-INC/ipro-sdk-releases) · [Documentation](https://intelpro-inc.github.io/ipro-sdk-docs/)
