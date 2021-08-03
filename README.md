# Two Tree Bluer

## Este repositório é para ser usado como modelo para compilar o firmware para bluer two tree

Baixar a ultima versão no site do marlin, até o momento 2.0.9.1
https://marlinfw.org/meta/download/

Baixar os arquivos de configuração de exemplo para Bluer Two Tree de acordo com versão do marlin
https://github.com/MarlinFirmware/Configurations/tree/release-2.0.9.1/config/examples/Two%20Trees

https://github.com/MarlinFirmware/Configurations/tree/release-2.0.9.1


O arquivo que deverá alterar e personalizar de acordo com a configuração desejada é Configuration.h, localizado em Marlin-2.0.x\Marlin\Configuration.h

```c
// No arquivo platformio.ini alterar a configuração dos envs.
default_envs = mks_robin_nano35_maple
```

```c
// Para habilitar o BLTouch descomentar a linha
#define BLUER_BLTOUCH // Enable if you want to use BLTOUCH
```

```c
  #if ENABLED(PID_PARAMS_PER_HOTEND)
    // Specify between 1 and HOTENDS values per array.
    // If fewer than EXTRUDER values are provided, the last element will be repeated.
    #define DEFAULT_Kp_LIST { 11.03, 11.03 }
    #define DEFAULT_Ki_LIST {  0.63,  0.63 }
    #define DEFAULT_Kd_LIST { 48.43, 48.43 }
  #else
    // Bluer
    // Altere as linhas abaixo de acordo com sua necessidade para configurar a temperatura do HOTEND
   -> #define DEFAULT_Kp 17.05
   ->#define DEFAULT_Ki 1.24
   -> #define DEFAULT_Kd 58.83
  #endif
```

```c
#if ENABLED(PIDTEMPBED)
    // Altere as linhas abaixo de acordo com sua necessidade para configurar a temperatura da Mesa
  -> #define DEFAULT_bedKp 39.84
  -> #define DEFAULT_bedKi 7.78
  -> #define DEFAULT_bedKd 135.99

  // FIND YOUR OWN: "M303 E-1 C8 S90" to run autotune on the bed at 90 degreesC for 8 cycles.
#endif // PIDTEMPBED
```