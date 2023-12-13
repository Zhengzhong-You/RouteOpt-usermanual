# Installation Guide for RouteOpt on macOS

Welcome to the RouteOpt installation guide for macOS. This document provides a step-by-step procedure for setting up the
RouteOpt environment and compiling the necessary components on a macOS system. Please follow the instructions carefully
to ensure a smooth installation process.

## Prerequisites

Before proceeding with the installation, ensure that you have administrative access to your system and an active
internet connection.

## Step 1: Install Homebrew

Homebrew is a package manager for macOS that simplifies the installation of software. Install it by running the
following command in the terminal:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

## Step 2: Install LLVM

LLVM is a collection of modular and reusable compiler and toolchain technologies. Install LLVM via Homebrew:

```bash
brew install llvm
```

## Step 3: Configure Environment Variables

Set the necessary environment variables for the ARM64 architecture by adding the following lines to
your `~/.bashrc`, `~/.zshrc`, or the respective shell configuration file:

```bash
export PATH="/opt/homebrew/bin:$PATH"
export PATH="/opt/homebrew/opt/llvm/bin:$PATH"
export LDFLAGS="-L/opt/homebrew/opt/llvm/lib"
export CPPFLAGS="-I/opt/homebrew/opt/llvm/include"
```

After updating the configuration file, apply the changes by running:

```bash
source ~/.bashrc  # or replace with your shell's respective config file
```

## Step 4: Install OpenMP

OpenMP is an API for multi-platform shared-memory parallel programming in C/C++. Install it using Homebrew:

```bash
brew install libomp
```

## Step 5: Compile xgboost

xgboost is an optimized distributed gradient boosting library. To compile it, follow these steps:

```bash
cd RouteOpt/dependency/xgboost  # Navigate to the xgboost directory within dependencies
mkdir build                     # Create a build directory
cd build                        # Enter the build directory
cmake ..                        # Generate make files
make -j$(sysctl -n hw.ncpu)     # Compile using all available cores
```

## Step 6: Compile cvrpsep

cvrpsep is a library for the separating capacity related cuts. To compile it:

```bash
cd RouteOpt/dependency/cvrpsep  # Navigate to the cvrpsep directory within dependencies
make -j$(sysctl -n hw.ncpu)     # Compile using all available cores
```

## Step 7: Compile hgs

hgs is a hybrid genetic search algorithm. To compile it:

```bash
cd RouteOpt/dependency/hgs      # Navigate to the hgs directory within dependencies
mkdir lib                     # Create a build directory
cmake .                         # Generate make files
make install                    # Compile and install
```

## Step 8: Compile RouteOpt

Finally, compile the RouteOpt application:

```bash
cd RouteOpt/(some application)  # Replace with the actual application path
cmake .                         # Generate make files
make -j$(sysctl -n hw.ncpu)     # Compile using all available cores
```

Trouble Shooting: the OpenMP library is not found, change the compiler to the one installed by Homebrew,
then replace ``cmake .`` with the following command:

```bash
cmake -DCMAKE_C_COMPILER=/opt/homebrew/opt/llvm/bin/clang -DCMAKE_CXX_COMPILER=/opt/homebrew/opt/llvm/bin/clang++ .
```

Or, you can add the following lines to your `~/.bashrc`, `~/.zshrc`, or the respective shell configuration file:

```bash
export CC=/opt/homebrew/opt/llvm/bin/clang
export CXX=/opt/homebrew/opt/llvm/bin/clang++
```

After following these steps, RouteOpt and all its dependencies should be compiled and installed on your macOS system. If
you encounter any issues, ensure that all steps were followed correctly, and check the console output for specific error
messages that can help in troubleshooting.

---

*Note: This guide assumes that the user is familiar with basic terminal operations. For more detailed explanations or
help, consult the official documentation for each of the tools or libraries involved.*