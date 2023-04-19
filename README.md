![image](https://user-images.githubusercontent.com/68618182/188527035-385752e7-fbd3-4865-abda-fdba4a804d99.png) ![image](https://user-images.githubusercontent.com/68618182/213734198-0cf50021-1f02-4c80-9a48-6f20ad42ce04.png)

# llvm-minimal-git

LLVM toolchain packages for Archlinux. (git version) (No docs, no unittest, no test) (Less build time) Also included in this repo spirv-headers, spirv-tools, glslang and mesa (mesa,lib32-mesa)

### SPIRV-Headers and SPIRV-Tools

This repo contain spirv-headers-git and spirv-tools-git package. Why so? Because SPIRV-LLVM-Translator depends on it. Easier to have it in this repo and compile them at the same time of compiling LLVM.

### glslang

This repo contain glslang-git package. Why so? Because glslang depends on SPIRV-Headers and SPIRV-Tools. So it feel more natural to have this package in this repo.

### Mesa

Why Mesa's packages are not in a separate repo? Because mesa and llvm are closely tied together, everytime llvm changes/updates, mesa needs to be rebuilt. Another reason is that, everytimes glslang version change, archlinux recompile mesa against glslang new version, so it feel more natural to have this package in this repo. If you want to just compile Mesa's packages and not interested about LLVM, SPIRV and glslang package you can go ahead, no problem.

#### 20/01/2023

mesa-git and lib32-mesa-git are not in minimal format yet. Will I do a minimal fortmat? Maybe.

# Version

### LLVM

- 17.0.0

- commit: 0acb639fd2350d831f149035e078654a655c209b

### SPIRV-LLVM-Translator

- 17.0.0

- commit : 548fc2d6cbcf5630035b8243b1b51329501d30e3

### SPIRV-Headers

- 1.5.4.raytracing.fixed

- commit : cfbe4feef20c3c0628712c2792624f0221e378ac

### SPIRV-Tools

- 2023.1

- commit : 25ad5e19f193429b737433d5f6151062ddbc1680

### glslang

- 12.1.0

- commit : 68f073b19569b580ecc7ba13fa96be3ecf65a0f6

### Mesa

- 23.2.0

- commit : 24555f5462e97e80ffe20f47a279d3c344fa6ea2

# Build

    git clone https://github.com/blacksky3/llvm-minimal-git.git
    cd llvm-git
    ./build.sh

### After succeful build

After a succeful build of the toolchain you'll need to recompile mesa package, because mesa and llvm are closely tied together. Everytime llvm changes/updates, mesa needs to be rebuilt.

    cd mesa/all/mesa-git
    makepkg -si

    cd mesa/all/lib32-mesa-git
    makepkg -si

# Prebuild package

Prebuild package are available at https://repo.blacksky3.com/x86_64/llvm-minimal-git

You can add this repo to your pacman.conf

    [llvm-minimal-git]
    SigLevel = Optional TrustAll
    Server = https://repo.blacksky3.com/$arch/$repo

    sudo pacman -S llvm-minimal-git llvm-libs-minimal-git clang-libs-minimal-git spirv-llvm-translator-minimal-git libclc-minimal-git lib32-llvm-minimal-git lib32-llvm-libs-minimal-git lib32-clang-libs-minitmal-git spirv-headers-git spirv-tools-git glslang-git

### Reinstall normal LLVM Toolchain

    sudo pacman -S llvm llvm-libs lib32-llvm lib32-llvm-libs clang lib32-clang compiler-rt libclc spirv-llvm-translator spirv-headers spirv-tools glslang

# Donation

BTC : bc1quz6zcjjy769cn9fd42r89hfh9unr4u2w4sfxer

ETH : 0xF8cBcA16f4eeDfF4a07D173B7fF53906a87b0476

DAI : 0xF8cBcA16f4eeDfF4a07D173B7fF53906a87b0476

LINK : 0xF8cBcA16f4eeDfF4a07D173B7fF53906a87b0476
