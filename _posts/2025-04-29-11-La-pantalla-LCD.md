---
layout: post
title: "11 - La pantalla LCD"
date: 2025-04-29 12:30:00 +0200
categories: arduino display
excerpt: "Aprender a usar una pantalla LCD de 16x02 para mostrar información en el monitor serial y en la propia pantalla."
---

## Finalidad

- Montaje de una pantalla LCD de 16x02
- Enviar información a la pantalla LCD
- Cómo definir caracteres especiales

## Material

| Imagen | Descripción |
| ------ | ----------- |
| ![Arduino Uno](/assets/images/material/mat_unor3.png) | Arduino UNO o compatible |
| ![Protoboard](/assets/images/material/mat_protoboard.png) | Protoboard |
| ![Cables](/assets/images/material/mat_cables.png) | Cables |
| ![Potenciómetro](/assets/images/material/mat_potenciometre.png) | Potenciómetro |
| ![LCD 16x02](/assets/images/material/mat_LCD16x02.png) | LCD 16x02 |

## Descripción del material

La pantalla LCD-1602 es una pantalla de cristal líquido de 16 caracteres de 2 líneas de baja potencia, con interfaz serie. Puedes descargar la hoja de características (en inglés)
[aquí](https://drive.google.com/file/d/1HBZ9CGzrnn9KpkAL3vX0qYVMRbhbbpwr/view?usp=sharing).

![pantalla-lcd](/assets/images/ard/ard_11_01.png)

Las pantallas LCD (Liquid Crystal Display) son una de las formas más sencillas y económicas de dotar de un display a un autómata.

El Hitachi HD44780 es uno de los controladores de LCDs más ampliamente extendidos por su sencillez y bajo precio. El HD44780 está diseñado para controlar LCDs monocromos de hasta 80 caracteres alfanuméricos y símbolos. También dispone de una pequeña memoria RAM para configurar nuestros propios caracteres o dibujos.

Las pantallas LCD con el controlador HD44770 se fabrican en diferentes tamaños, siendo comunes 16x02 (2 líneas de 16 caracteres), 20x02, 20x04 y 40x02.

Las pantallas LCD disponen de retroiluminación posterior en azul o en verde. El contraste puede ser variado conectando un potenciómetro al LCD.

Conectar directamente un LCD a Arduino requiere una gran cantidad de pines. Suele ser aconsejable emplear un **adaptador a bus I2C**, como veremos en la próxima entrada.

## Montaje

![esquema-montaje](/assets/images/ard/ard_11_02.png)
![esquema-electric](/assets/images/ard/ard_11_03.png)

Como podéis ver son necesarios un buen número de cables para hacer las conexiones, así que es muy fácil equivocarse. Por eso se recomienda utilizar un módulo I2C, que simplifica muchísimo el montaje.

La relación de los pines y su conexión tanto para el arduino como para la pantalla es la siguiente:

|          | LCD                                        | Arduino              |
| :------- | :----------------------------------------- | :------------------- |
| 01 - GND | negativo pantalla                           | GND                  |
| 02 - Vcc | positivo pantalla                           | 5V                   |
| 03 - V0  | ajuste del contraste                        | Pot 10K pin variable |
| 04 - RS  | registro de señal de selección             | Pin 12               |
| 05 - R/W | señal de selección de lectura / escritura  | GND                  |
| 06 - E   | señal de activación de operación           | Pin 11               |
| 07 - D0  |                                            |                      |
| 08 - D1  |                                            |                      |
| 09 - D2  |                                            |                      |
| 10 - D3  |                                            |                      |
| 11 - D4  | Transferencia de datos                     | Pin 05               |
| 12 - D5  | Transferencia de datos                     | Pin 04               |
| 13 - D6  | Transferencia de datos                     | Pin 03               |
| 14 - D7  | Transferencia de datos                     | Pin 02               |
| 15 - A   | iluminación de fondo                       | 5V                   |
| 16 - K   | iluminación de fondo                       | GND                  |

---

## Programación

Para este montaje subiremos el ejemplo contenido en «Archivo>Ejemplos>LiquidCrystal>Hello world».

La librería necesaria para controlar la pantalla LCD se llama «LiquidCrystal» y puedes consultar la referencia en el enlace <https://www.arduino.cc/en/Reference/LiquidCrystal>

```Arduino

Código: ARD_11.ino

#include <LiquidCrystal.h>  // incluye el código de la biblioteca

// inicializa la biblioteca asociando cualquier pin de interfaz LCD necesario al número de pin arduino al que esté conectado

const int rs = 12, en = 11, d4 = 5, d5 = 4, d6 = 3, d7 = 2;
LiquidCrystal lcd(rs, en, d4, d5, d6, d7);

void setup()
{

  lcd.begin(16, 2);  // configura el número de columnas y filas de la pantalla LCD
  lcd.print("hello, world!");  // Escribe un mensaje en la pantalla LCD

}

void loop()
{

  lcd.setCursor(0, 1);  // posiciona el cursor en la columna 0, línea 1 (Nota: la línea 1 es la segunda fila, ya que el conteo comienza por 0)
  lcd.print(millis() / 1000);  // imprime el número de segundos desde el reinicio

}
```

## Definiendo tus propios caracteres

Definiremos un carácter propio, el símbolo de grados centígrados, por ejemplo.

Lo primero que debes saber, es que los caracteres se definen con un array de 8×8, como si los dibujaras en una cuadrícula de ese tamaño, y rellenando el cuadradito pertinente.

Así por ejemplo para el símbolo del grado sería:

![figura-grado](/assets/images/ard/ard_11_04.png)

Antes del setup(), en las declaraciones y definiciones es donde creamos los caracteres personales.

```Arduino

byte grado[8] =
{
  0b00001100, // _Los definimos como binarios_ 0bxxxxxxx
  0b00010010,
  0b00010010,
  0b00001100,
  0b00000000,
  0b00000000,
  0b00000000,
  0b00000000
};
```

Para montar los caracteres definidos usamos:

```Arduino

lcd.createChar(0, euro);
lcd.createChar(1, grado);
```

Y ahora ya están disponibles. Ten en cuenta que solo podemos definir 8 caracteres especiales en un momento dado

Aquí tenemos un ejemplo de código:

```Arduino

#include <LiquidCrystal.h>
LiquidCrystal lcd(_12_, _11_, _5_, _4_, _3_, _2_);

byte grado[8] =
{
  0b00001100,
  0b00010010,
  0b00010010,
  0b00001100,
  0b00000000,
  0b00000000,
  0b00000000,
  0b00000000
};

void setup()

{
  lcd.begin(16, 2); // inicializar el LCD
  lcd.createChar(1, grado); // crea el carácter grado
  lcd.setCursor(0, 0); // posiciona el cursor
  lcd.print("Estamos a 25 "); // mensaje
  lcd.write(1); // escritura del carácter personal
}

void loop()

{

}
```

## Conceptos importantes

- Conocer las pantallas LCD
- Comprender la conexión con arduino
- Aprender a crear nuestros propios caracteres.
