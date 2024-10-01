# fe8-chax-template

## Usage

1. You must have a linux environment such as **WSL** or ubuntu server.
2. Build dependence
    ```bash
    sudo apt-get -y install binutils-arm-none-eabi \
        gcc-arm-none-eabi build-essential cmake re2c ghc \
        cabal-install libghc-vector-dev libghc-juicypixels-dev \
        python3-pip pkg-config libpng*

    pip install pyelftools PyInstaller tmx six
    ```
3. Update submodules
    ```bash
    cd Tools
    git clone https://github.com/MokhaLeee/FE-CLib-Mokha.git
    git clone https://github.com/MokhaLeee/EventAssembler.git -b mokha-fix
    ```
4. Build **EventAssembler**

    Get into **Tools/EventAssembler** and then refer to [EA build note](https://github.com/StanHash/EventAssembler)

    ```bash
    # Install .NET
    # refer to: https://learn.microsoft.com/en-us/dotnet/core/install/linux-scripted-manual#scripted-install
    wget https://dot.net/v1/dotnet-install.sh -O dotnet-install.sh
    chmod +x ./dotnet-install.sh
    sudo ./dotnet-install.sh --channel 6.0
    
    export DOTNET_ROOT=$HOME/.dotnet
    export PATH=$PATH:$DOTNET_ROOT:$DOTNET_ROOT/tools
    
    # Build EA
    cd Tools/EventAssembler
    ./build.sh
    ```

5. Put **Fire Emblem: The Sacred Stones** clean rom named `fe8.gba` in the repository directory.
6. Write your own **.c** or **.s** file inside **./wizardry** and add them to **./wizardry/wizardry.event**
7. `make -j` and then you may get a `fe8-chax.gba`

## See also

* [**FE8U-CSkillSys**](https://github.com/FireEmblemUniverse/fe8u-cskillsys), project to insert everything through EA for CHAX.
* [**FireEmblemUniverse/fireemblem8u**](https://github.com/FireEmblemUniverse/fireemblem8u), a decompilation of Fire Emblem: The Sacred Stones (US)
