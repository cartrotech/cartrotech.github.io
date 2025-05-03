---
layout: post
title: "12 - El módulo de pulsador"
date: 2025-04-30 12:00:00 +0200
categories: arduino actuadores
excerpt: "Aprender a usar un módulo de pulsador para controlar un LED."
---

## Finalidad

- Cómo utilizar los pulsadores

## Material

| Imagen | Descripción |
| ------ | ----------- |
| ![Arduino Uno](/assets/images/material/mat_unor3.png) | Arduino UNO o compatible |
| ![Protoboard](/assets/images/material/mat_protoboard.png) | Protoboard |
| ![Cables](/assets/images/material/mat_cables.png) | Cables |
| ![Módulo pulsador](/assets/images/material/mat_KY004.jpeg) | Módulo pulsador |

## Descripción del material

### Pulsadores

Los conmutadores son componentes realmente simples. Cuando presionas un botón o giras una palanca, conectan dos contactos juntos para que la electricidad pueda circular por ellos. Un _pulsador_ es un conmutador que vuelve a la posición de reposo cuando dejamos de actuar sobre él.

Los pequeños interruptores táctiles que se utilizan en esta lección tienen cuatro conexiones, lo que puede ser un poco confuso.

![Pulsador y esquema](/assets/images/ard/ard_12_01.png)

En realidad, solo hay realmente dos conexiones eléctricas, ya que dentro del paquete de interruptores los pines B y C están conectados juntos, igual que A y D.

### Módulo pulsador

Una resistencia de 10 K ohm incorporada está conectada entre el pin central y el pin "S" y se puede utilizar como resistencia de pull-up o pull-down. El pulsador conecta los dos pines externos.

![Módulo pulsador](/assets/images/ard/ard_12_02.png)

## Montaje

Vamos a hacer que el LED integrado en la placa Arduino y conectado al pin 13 parpadee cuando pulsemos el botón. Para conseguirlo hay que cablear la «output» del módulo al pin 3 de Arduino, la Vcc con 5V y Gnd con Gnd. Como veis el montaje es muy sencillo.

![Esquema eléctrico](/assets/images/ard/ard_12_03.png)
![Montaje](/assets/images/ard/ard_12_04.png)

## Programación

```Arduino

/*
CARTROTECH (https://cartrotech.github.io)
Proyecto nº: ARD012
Fecha: 29.08.2021
Descripción: Leer un pulsador y hacer parpadear el LED del pin 13
*/

int Led = 13; //Asigna el pin Led
int pols = 3; //Asigna el pin al pulsador
int val; //Define una variable

void setup()
{
    pinMode(Led, OUTPUT); //Configura el pin 13 (Led) como salida
    pinMode(pols, INPUT); //Configura el pin 3 (puls) como entrada
}

void loop()
{
    val = digitalRead(pols); //lee el valor de la entrada 3 y lo asigna a val
    if (val == HIGH)
    {
        digitalWrite (Led,LOW);
    }
    else
    {
        digitalWrite (Led,HIGH);
        delay(200);
        digitalWrite (Led,LOW);
        delay(200);
    }
}
```

## Conceptos importantes

- Seguimos utilizando las resistencias pull-up o pull-down cuando usamos pulsadores
- Hemos aprovechado parte del código del blinking led en este programa.
