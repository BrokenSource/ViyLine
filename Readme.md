πγβ°γTable of Contents

<div align="center">
  <img src="https://github.com/BrokenSource/ViyLine/raw/Master/ViyLine/icon.png" onerror="this.src='../ViyLine/icon.png'" width="256"/>

    ViyLine - Vee Aye Line

  Solar panel IV curve tracker using a PIC16F877A Microcontroller, HC-06 Bluetooth module and a front end GUI in Rust.

</div>

<br>

<sub><b>NOTE:</b> This is a VERY DIY project, you will be building the physical circuit itself, we provide you the schematic and list of components.</sub>

<br>

<img src="https://user-images.githubusercontent.com/29046864/206887190-394abf94-4711-4895-99ae-ba2229928477.png"/>



# β The Project: Briefly explained
- Every Solar Panel has a characteristic current-voltage curve it can output at either value being limited. The two magical points are the **open circuit voltage** and **short circuit voltage**.

- The curve changes with variations in luminosity and temperature, and can be used as a diagnosis of efficiency or any broken panel indication.

- The curve also gives the rated power output and the point of maximum efficiency, called the Maximum Power Point (MPP).

Collecting these points requires a variable load that ranges from short circuit to open circuit and the ability to measure pairs of voltage and current points throughout the process, sweeping all possible loads.

A microcontroller is used to measure the points and send signals to MOSFETs to either charge or discharge a capacitor, acting as a variable load when charging.

The points are sent back to the Rust code using either Serial or Bluetooth communication, and a non linear regression is applied to generate the best prediction of the real IV curve being measured.

Read our [Paper](https://github.com/BrokenSource/ViyLine/raw/Master/Paper/Paper.pdf) for more details!


# β Running from Source Code

1. Follow the **Running from Source Code** bootstrap from [Protostar](https://github.com/BrokenSource/Protostar) Monorepo.

2. Building the Assembly
    - You'll need to download MPLAB and compile the `.asm` code with `MPASMWIN.exe` to generate the `.hex` sent to the microcontroller.
    - Copy `C:\\Program Files (x86)\Microchip\MPASM Suite` to `./Assembly/Thirdparty/MPASM Suite`.
    - Either run `Compile.sh` in Linux/MacOS or on Windows open a PowerShell and run `".\MPASM Suite\MPASMWIN.exe" /q /p16F877A "ViyLineCAP.asm"`

Bluetooth connectivity can be achieved by pairing the HC06 and using its COM port available from the OS, otherwise you'll need to use an UART/USB serial cable communication.

# β Building the Circuit
The circuit schematic will be provided at some point in the close future.


## List of Components
- 1x MicrochipΒ© PIC16F877A Microcontroller
- 1x HC-06 Bluetooth module
- 1x ManyFaradsAsPossibleβ’ Capacitor *that doesn't kill you*
- 1x UART USB for writing the hexadecimal on the PIC
- A computer with bluetooth and any recent OS

Full list of components will be provided at some point in the close future.



# β License
All credits to MicrochipΒ© on their respective names of `PIC`, `MPASM` and included libraries.

ViyLine code falls under the `MIT` License. The logos, schematics are under CC-BY-4.0.



# β Citing

BibTeX entry for LaTeX:
```bibtex
@electronic{viyline,
  title    = {ViyLine: TraΓ§ador de Curva IV do Painel Solar},
  keywords = {Rust, PIC, Assembly, Solar Panel, IV Curve},
  url      = {https://github.com/BrokenSource/ViyLine},
  author   = {Tremeschin; et al.},
  year     = {2022},
  abstract = {
    Pronunciado Vee-Aye-Line, este software escrito em
    Assembly e Rust, disponibilizado em CΓ³digo Aberto, utilizando
    o microcontrolador da MicrochipΒ© PIC16F877A coleta pontos da
    Curva IV caracterΓ­stica de um Painel Solar com tensΓ΅es atΓ© 50V
    e corrente atΓ© 5A. Seu circuito de mediΓ§Γ£o Γ© composto por
    capacitores, que atuam como uma carga variΓ‘vel para a coleta
    de pontos da curva. TambΓ©m possui uma interface grΓ‘fica e
    funciona com cabo USB Serial UART ou pelo mΓ³dulo Bluetooth
    HC-06 para o envio de sinais e recebimento de dados. Possui
    uma modelagem matemΓ‘tica por mΓ©todos computacionais para melhor
    precisΓ£o dos dados exportados pela ferramenta, realizando uma
    regressΓ£o nΓ£o linear para ajuste de curva dos pontos medidos
    em relaΓ§Γ£o Γ  curva teΓ³rica de operaΓ§Γ£o de um painel solar, a
    fim de mitigar imprecisΓ΅es de mediΓ§Γ£o utilizando-se da estatΓ­stica.
  },
}
```