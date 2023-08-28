# Configuração da Scarlet

Esse respositório é responsável por armazenar a configuração da impressora 3D do Laboratório de Automação e Robótica (LAR), situado na Universidade Federal do Rio Grande Do Norte.

## Passo a passo do firmware

O firmware atual está na versão 2.0.x do marlin, disponível no site da própria desenvolvedora, o qual é baseado no conceito de código aberto onde você mesmo pode criar a sua impressora e utilizar os diversos recursos que esta plataforma oferece.

### Pontos Chaves
```c++
  /**
  *  Seção relacionada ao movimento da máquina.
  */

  #define DEFAULT_AXIS_STEPS_PER_UNIT   { 80, 80, 400, 87.05 }

  #define DEFAULT_MAX_FEEDRATE          { 500, 500, 80, 45 }

  #define DEFAULT_MAX_ACCELERATION      { 2000, 2000, 100, 10000 }

  #define DEFAULT_ACCELERATION          10000    // X, Y, Z ... and E acceleration for printing moves
  #define DEFAULT_RETRACT_ACCELERATION  800    // E acceleration for retracts
  #define DEFAULT_TRAVEL_ACCELERATION   1000    // X, Y, Z ... acceleration for travel (non printing) moves

  #define CLASSIC_JERK
  #define DEFAULT_XJERK 15.0
  #define DEFAULT_YJERK 15.0
  #define DEFAULT_ZJERK  0.4

  #define DEFAULT_EJERK    8.5  // May be used by Linear Advance

  /**
  *  Seção relacionada à estrutura.
  */
  // Choose the name from boards.h that matches your setup
  #ifndef MOTHERBOARD
    #define MOTHERBOARD BOARD_RAMPS_14_EFB
  #endif

  #define X_DRIVER_TYPE  A4988
  #define Y_DRIVER_TYPE  A4988
  #define Z_DRIVER_TYPE  A4988
  #define E0_DRIVER_TYPE A4988

  #define Z_MIN_PROBE_USES_Z_MIN_ENDSTOP_PIN

  #define X_HOME_DIR -1
  #define Y_HOME_DIR -1
  #define Z_HOME_DIR -1

  // The size of the printable area
  #define X_BED_SIZE 200  
  #define Y_BED_SIZE 200

  // Travel limits (mm) after homing, corresponding to endstop positions.
  #define X_MIN_POS -9
  #define Y_MIN_POS -58
  #define Z_MIN_POS 0
  #define X_MAX_POS X_BED_SIZE
  #define Y_MAX_POS Y_BED_SIZE
  #define Z_MAX_POS 200

  #define MESH_BED_LEVELING
  #elif ENABLED(MESH_BED_LEVELING)

    //===========================================================================
    //=================================== Mesh ==================================
    //===========================================================================
  
    #define MESH_INSET 10          // Set Mesh bounds as an inset region of the bed
    #define GRID_MAX_POINTS_X 4    // Don't use more than 7 points per axis, implementation limited.
    #define GRID_MAX_POINTS_Y GRID_MAX_POINTS_X
  
    //#define MESH_G28_REST_ORIGIN // After homing all axes ('G28' or 'G28 XYZ') rest Z at Z_MIN_POS
  
  #endif // BED_LEVELING

  #define LCD_BED_LEVELING

  #define REPRAP_DISCOUNT_FULL_GRAPHIC_SMART_CONTROLLER // Utilizando a biblioteca U8glib
```

### Personalização

```c++
  // Show the Marlin bootscreen on startup. ** ENABLE FOR PRODUCTION **
  #define SHOW_BOOTSCREEN

  // Show the bitmap in Marlin/_Bootscreen.h on startup.
  #define SHOW_CUSTOM_BOOTSCREEN
  
  // Show the bitmap in Marlin/_Statusscreen.h on the status screen.
  #define CUSTOM_STATUS_SCREEN_IMAGE

  // Name displayed in the LCD "Ready" message and Info menu
  #define CUSTOM_MACHINE_NAME "Scarlet"

  // Printer's unique ID, used by some programs to differentiate between machines.
  // Choose your own or use a service like https://www.uuidgenerator.net/version4
  #define MACHINE_UUID "359ff4ba-4109-11ee-be56-0242ac120002"
```

### Imagens Personalizadas
#### Bootscreen
![teste](https://raw.githubusercontent.com/BigLeno/Scarlet/main/Imagens/Logo%20-%20LAR%20Impressora.bmp)

#### Statusscreen
![teste](https://raw.githubusercontent.com/BigLeno/Scarlet/main/Imagens/Status.bmp)

## Guia do Fatiador

A seguir estão contidos o passo à passo de como configurar e utilizar a impressora no Fatiador, no exemplo, Ultimaker cura, que estava na versão 5.4.

![teste](https://raw.githubusercontent.com/BigLeno/Scarlet/main/Configuração%20do%20Cura/cura.png)

## Referência

 - [Ultimaker cura](https://ultimaker.com/software/ultimaker-cura/)
 - [Marlin](https://marlinfw.org/)
 - [LAR](http://www.natalnet.br/lar/index.php/contato/)
