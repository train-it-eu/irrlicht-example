# "Modern C++ Design: Part I" Workshop Preparation

## Development Environment Setup

### Docker

The workshop is intended to run on a [Docker](https://www.docker.com) container based on a provided image.
The image provides gcc, clang, CMake, Ninja, debuggers, clang-format, pre-configured [Conan package manager](https://conan.io),
and more...

To install [Docker](https://www.docker.com):
- [Windows or Mac OS] Download [Docker Desktop](https://www.docker.com/products/docker-desktop).
- [Linux] Please use your system's package manager.

### XServer

[Irrlicht](http://irrlicht.sourceforge.net) is an open source realtime 3D engine written in C++. In order to
see the graphics we will need to export docker container's display to the host's XServer.

#### Windows

1. Install [VcXsrv Windows X Server](https://sourceforge.net/projects/vcxsrv).
2. Run `XLaunch` from the start menu and follow the configuration steps:
    - `Next` on "Display settings"
    - `Next` on "Client startup"
    - Check "Disable access control" on "Extra settings" and `Next`
    - `Finish` on "Finish configuration"

#### Linux & Mac OS

Make sure that you know how to redirect display from a container running Ubuntu image to your XServer
(e.g. `export DISPLAY=<your PC's IP address>:0.0`).

### Visual Studio Code

The usage of [Visual Studio Code](https://code.visualstudio.com/download) is strongly suggested for this workshop.
Make sure to enable at least the following extensions:
- [C/C++ Extension Pack](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cpptools-extension-pack)

### Alternative Development Environments

You can try to use your own development environment for this workshop but in such a case please make sure that you:
- Have a C++20-ready compiler
- Installed [Conan package manager](https://conan.io) and provided a profile for your compiler
- [Windows only] installed [DirectX SDK](https://www.microsoft.com/en-us/download/details.aspx?id=6812)
- Can compile and run the provided example.


## Compilation

1. When you open this folder in a VSCode it will ask:

    _Folder contains a Dev Container configuration file. Reopen folder to develop in a container (learn more)._

    Click `Reopen in Container` and wait a moment for the container to initialize.

2. After opening in the container the VSCode will ask which toolchain to use for CMake. Please select the latest gcc.

3. The project will fail to compiler because of unmet [Conan package manager](https://conan.io) dependencies.
    Switch to `TERMINAL` tab in VSCode and open a new bash shell by clicking `+`. In the new shell please do the
    following:
    - `cd build/<your_cmake_toolchain>`
    - `conan install ../..`

4. Build the project.
