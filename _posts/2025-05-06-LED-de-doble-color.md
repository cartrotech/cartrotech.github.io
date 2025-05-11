---
layout: post
title: "LED de doble color"
date: 2025-05-06 19:00:00 +0200
categories: arduino actuadores
excerpt: "Conoce el funcionamiento del LED de doble color y cómo usarlo en tus proyectos Arduino."
---

## Objetivo

- Conocer y comprender el funcionamiento del LED de doble color

## Material

|                                  Imagen                                  | Descripción                    |
| :----------------------------------------------------------------------: | :---------------------------- |
|    ![Arduino Uno](/assets/images/material/mat_unor3.png)     | Arduino Uno o equivalente.     |
|  ![Protoboard](/assets/images/material/mat_protoboard.png)  | Protoboard                    |
|    ![Cables](/assets/images/material/mat_cables.png)    | Cables de conexión            |
|    ![Módulo LED doble color](/assets/images/material/mat_KY029.png)    | Módulo LED dos colores (KY-029) |
| ![Resistencias](/assets/images/material/mat_resistencia.jpeg) | 2 Resistencias 220 o 330 Ω    |

## Descripción

Módulo LED de 5 mm de doble color para Arduino (KY-029), emite luz roja
y verde. Puede ajustar la cantidad de cada color usando PWM. Este módulo
es similar al KY-011. El pin "R" representa el color rojo y el pin
"Y" representa el color verde, el pin G se conecta a GND.

## Características

Este módulo consta de un LED rojo/verde de cátodo común de 5 mm y sin
resistencia. Utilice este módulo con algunas resistencias limitadoras
para evitar que el LED se queme cuando trabaje durante largos períodos de
tiempo.

- Voltaje de trabajo: 2,3-2,6 V para verde, 1,9-2,2 V para rojo
- Corriente de trabajo: 20mA
- Diámetro: 5 mm
- Encapsulado: Difusión
- Color: rojo/verde
- Longitud de onda: 571 / 625nm
- Intensidad luminosa: 20~40, 60~80 mcd

## Diagrama de conexión

Usaremos un par de resistencias de 220-330Ω para limitar la corriente
del Arduino y evitar que se queme el LED.

| Módulo | Arduino              |
| ----- | -------------------- |
| G     | GND                  |
| R     | 330Ω resistor Pin 11 |
| Y     | 330Ω resistor Pin 10 |

![Montaje módulo LED doble color](/assets/images/ard/ard_19_01.png)

## Programación

El siguiente código de Arduino alternará gradualmente entre el color rojo y
verde.

```Arduino
/*
* CartroTech (https://cartrotech.github.io)
*
* Proyecto nº: ARD019
* Fecha: 24.10.2021
* Descripción: Funcionamiento del LED de doble color
* Nota:
*
*/

int redpin = 11; // pin para el LED rojo
int greenpin = 10;// pin para el LED verde
int val;

void setup()
{
  pinMode(redpin, OUTPUT); //definimos el pin rojo como salida
  pinMode(greenpin, OUTPUT); //definimos el pin verde como salida
  Serial.begin(9600); //iniciamos el puerto de comunicación serial
}

void loop()
{
  for(val = 255; val > 0; val--) //secuencia de paso de rojo a verde
  {
    analogWrite(redpin, val);
    analogWrite(greenpin, 255 - val);
    delay(10);
  }
  Serial.println("Verde"); //escribimos al puerto serie el color activo: verde
  delay(1000);
  for(val = 0; val < 255; val++) //secuencia de paso de verde a rojo
  {
    analogWrite(redpin, val);
    analogWrite(greenpin, 255 - val);
    delay(10);
  }
  Serial.println("Rojo"); //escribimos al puerto serie el color activo: rojo
  delay(1000);
}
```
