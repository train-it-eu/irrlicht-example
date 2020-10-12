# [Modern C++ Design: Part I](https://train-it.eu/trainings/cpp/27-modern-cpp-design-part-1) Workshop Preparation

## Development Environment Setup

### Docker

The workshop is intended to run on a [Docker](https://www.docker.com) container based on a provided image. The image
provides gcc, clang, CMake, Ninja, debuggers, clang-format, pre-configured [Conan package manager](https://conan.io),
and more...

To install [Docker](https://www.docker.com) please follow the point #1 of a detailed installation instruction in
[Developing inside a Container](https://code.visualstudio.com/docs/remote/containers#_installation) section of VSCode
documentation.

_Note:_ [WSL 2](https://docs.microsoft.com/en-us/windows/wsl) improves the performance of [Docker](https://www.docker.com)
on Windows. It is also a really powerful tool for daily C++ programming use. If you do not use it currently, please
consider installing it.

### XServer

[Irrlicht](http://irrlicht.sourceforge.net) is an open source realtime 3D engine written in C++. In order to
see 3D graphics we will need to export docker container's display to the host's XServer.

#### Windows

1. Install [VcXsrv Windows X Server](https://sourceforge.net/projects/vcxsrv).
2. Run `XLaunch` from the start menu and follow the configuration steps:
    - `Next` on "Display settings"
    - `Next` on "Client startup"
    - Check "Disable access control" on "Extra settings" and `Next`
    - `Finish` on "Finish configuration"
3. Uncomment appropriate line in "remoteEnv" part of `devcontainer.json` file.

#### Mac OS

1. Install [XQuartz](https://www.xquartz.org) and use it in a similar way as in the above Windows case.
2. Uncomment appropriate line in "remoteEnv" part of `devcontainer.json` file.

#### Linux

1. Run the following command

```bash
xhost +SI:localuser:root
```

2. Uncomment appropriate line in "remoteEnv" part of `devcontainer.json` file.

### Visual Studio Code

The usage of [Visual Studio Code](https://code.visualstudio.com/download) is strongly suggested for this workshop.
Make sure to enable at least the following extensions:
- [C/C++ Extension Pack](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cpptools-extension-pack)

### Alternative Development Environments

You can try to use your own development environment for this workshop but in such a case please make sure that you:
- have a C++20-ready compiler,
- installed [Conan package manager](https://conan.io) and provided a profile for your compiler
- [Windows only] installed [DirectX SDK](https://www.microsoft.com/en-us/download/details.aspx?id=6812)
- can compile and run the provided example.


## Compilation

1. When you open this folder in a VSCode it will ask:

    _Folder contains a Dev Container configuration file. Reopen folder to develop in a container (learn more)._

    - If on Windows and [WSL 2](https://docs.microsoft.com/en-us/windows/wsl) is not available:
      - choose `Clone in Volume`,
      - either provide a clone URL directly (https://github.com/train-it-eu/irrlicht-example.git) or choose
        "Clone a repository form GitHub in a Container Volume", and type "train-it-eu/irrlicht-example",
      - choose a volume for the repository (unique, current, other).
    - Otherwise, choose `Reopen in Container`.

2. Wait a moment for the container to initialize.

3. After opening the project in the container the VSCode will ask which toolchain to use for CMake. Please
    select the latest gcc.

4. The project will fail to compile because of unmet [Conan package manager](https://conan.io) dependencies.
    Switch to `TERMINAL` tab in VSCode (click `+` to open a new bash shell if needed). In the new shell please
    type the following:
    - `cd build/<your_cmake_toolchain>`
    - `conan install ../..`

5. Build the project.

6. Run the example app (choose "Software Renderer" in case of a Docker container usage).
