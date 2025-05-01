---
layout: post
title: "05 - Las entradas analógicas"
date: 2025-04-25 23:30:00 +0200
categories: arduino basic
excerpt: "En esta lección aprenderemos sobre las entradas analógicas de Arduino, con especial énfasis en el uso de potenciómetros. Veremos cómo funciona la conversión analógica-digital, cómo leer valores analógicos con Arduino y entenderemos las limitaciones de velocidad y resolución de los convertidores ADC."
---

[img1]: /assets/images/ard/ard_05_01.png "Esquema eléctrico"
[img2]: /assets/images/ard/ard_05_02.png "Conexión de un potenciómetro"
[img3]: /assets/images/ard/ard_05_03.png "Conversión analógica-digital"
[img4]: /assets/images/ard/ard_05_04.png "Entradas analógicas"
[img5]: /assets/images/ard/ard_05_05.png "Esquema de montaje"
[img6]: /assets/images/ard/ard_05_06.png "Salida por el monitor serie"

## Objetivos

- Conocer los potenciómetros.
- Comprender la conversión analógica a digital.
- Aprender a usar las puertas analógicas de Arduino.

## Material requerido

| Elemento | Descripción |
|----------|-------------|
| ![Arduino Uno](/assets/images/material/mat_unor3.png) | Arduino Uno o compatible |
| ![Protoboard](/assets/images/material/mat_protoboard.png) | Una protoboard |
| ![Cables](/assets/images/material/mat_cables.png) | Cables de connexión |
| ![LED](/assets/images/material/mat_led.png) | Un diodo led |
| ![Resistencia](/assets/images/material/mat_resis330.png) | Una resistencia 330 Ohms |
| ![Pulsador](/assets/images/material/mat_potenciometre.png) | Un potenciómetro  |

## Los potenciómetros

Hasta ahora hemos usado siempre resistencias fijas, de un valor dado. Pero a veces es conveniente disponer de una señal variable para controlar el circuito que nos interesa. Imagina el volumen de un equipo de música, o el dial que sintoniza una emisora en una radio FM.

Un potenciómetro es, simplemente, un mecanismo para proporcionar una resistencia variable.

Hay potenciómetros de tantos tamaños, formas y colores como puedas imaginar, pero al final son una resistencia fija de un valor dado (10 kΩ en nuestro caso actual) y un mecanismo que permite deslizar un dial conductor sobre esa resistencia, que nos permite tomar una parte de ese valor.

Por eso un potenciómetro siempre tiene 3 pines en fila. Los de los extremos se comportan como una resistencia del valor de fondo de escala del potenciómetro, y un pin central que va tomando valores de resistencia en función del movimiento que hacemos con el ajuste.

Montaremos un circuito como este (en el cual el potenciómetro está etiquetado Pot1):

![Esquema eléctrico][img1]

La idea es conectar 5V y GND a los extremos del Potenciómetro (no importa cuál es uno y cuál otro) y luego conectar el pin central al positivo de un LED y el negativo a GND directamente, pasando por una resistencia de limitación.

De esta manera cuando giramos el potenciómetro estaremos modificando la tensión que aplicamos a la entrada del LED, que variará entre 0 y 5V (Aunque ahora parezca extraño es muy sencillo) y habremos conseguido un regulador de intensidad del LED.

- _Con una resistencia de 10k la intensidad en el circuito será de: 5V / 10.000Ω = 0,5 mA. Muy poco para conseguir iluminar el LED que requiere unos 20 mA. Así que durante la mayor parte del giro del potenciómetro el LED estará apagado._
- _Importante: No olvides la resistencia R1. Aunque el potenciómetro limite la intensidad, hay un momento en que llegará a cero y aquí tu LED morirá en acto de servicio._

## Circuito para protoboard

El montaje en la protoboard sería similar a esto ya que utilizaremos el Arduino simplemente para dar tensión al circuito y nada más. Verás que la intensidad de la luz varía de manera continua al girar el potenciómetro.

![Potenciómetro más led][img2]

- _Recuerda que a causa del exceso de resistencia del potenciómetro de prueba, durante la mayor parte del giro del ajuste el LED estará apagado._
- _Nótese que en este caso utilizamos nuestro Arduino simplemente como fuente de alimentación para dar tensión al circuito._

## Arduino y las entradas analógicas

Con Arduino hemos visto que podemos influir en el mundo exterior aplicando salidas todo/nada en los pines digitales y también que usando PWM podemos simular bastante satisfactoriamente señales analógicas en algunos de esos pines.

También hemos visto cómo detectar pulsaciones de botones, definiendo como entradas los pines digitales. Pero en muchas ocasiones los sensores que usamos para supervisar el mundo exterior, nos entregan una señal analógica. Es el caso de los sensores de temperatura o distancia, de presión, de intensidad de corriente en un circuito o de caudal de agua en una tubería.

Para leer este tipo de señales continuas necesitamos un convertidor analógico a digital (o ADC por sus siglas en inglés) y que nos permita leer el valor de una señal analógica en un momento dado.

Estos convertidores toman una muestra del valor actual de la señal y nos entregan su _valor instantáneo_, medido en Voltios.

Mediante la lectura repetida de muestras a lo largo del tiempo podemos reconstruir la señal original con mayor o menor precisión, dependiendo de la exactitud de nuestra medida y de la velocidad a la que pueda tomar esas muestras.

![Conversión analógico-digital][img3]

Arduino UNO dispone de seis convertidores analógico a digital, nombrados de A0 hasta A5, etiquetados como ANALOG IN:

![Entradas analógicas][img4]

Veamos cómo usar las entradas analógicas con un circuito como este, en el cual damos tensión a los extremos de un potenciómetro y conectamos el pin central (el variable) a la entrada de la puerta A5 de Arduino:

![Esquema de montaje][img5]

- _Parece buen momento para destacar que los convertidores ADC leen valores de tensión y no resistencia, por tanto, lo que leeremos es **la caída de tensión** en el potenciómetro a medida que giramos el ajuste._

La primera curiosidad es que no necesitamos declarar en el **setup()** que usaremos una puerta analógica. Y la segunda es que para tomar una muestra (leer) del pin A5, usaremos la instrucción:

`int Val = analogRead(A5);`

- Los convertidores de Arduino UNO y Mega son de 10 bits de resolución por lo que nos retornará valores entre 0 y 2^10 = 1.024 para tensiones entre 0 y 5V. En cambio el Arduino DUE dispone de convertidores de 12 bits por lo que el valor de sus lecturas estará entre 0 y 2^12 o sea 4.096, es decir tiene mejor resolución (pero solo puede leer hasta 3,3V).
- Asegúrate de no usar sensores que puedan dar más de 5V máximo (con Arduino UNO y Mega), ya que dañarías el chip principal de Arduino.

Escribiremos un programa que lea el valor del pin A5 y lo envíe a la consola para que podamos visualizarlo.

## Usando las puertas analógicas

Prueba este programa:

```Arduino
/*
 * CARTROTECH  (https://cartrotech.github.io)
 * 
 * Projecto nº: ARD_05_01
 * Descripcion: Lectura de entradas analógicas
 * 
 * Fecha: 2025-04-25
 */

void setup()
{
    Serial.begin(9600); // Iniciamos la puerta serie
}

void loop()
{
    int Lectura = analogRead(A5);
    Serial.println(Lectura);
    delay(200);
}
```

Cuando lo vuelcas, arranca la consola y verás que a medida que giras el ajuste las lecturas varían de manera continua reflejando la posición del potenciómetro, las lecturas reflejan la caída en voltios.

![Monitor serie][img6]

No puedo resistirme a proponeros esta prueba: Desconecta el potenciómetro de la puerta A5 y observa los resultados que Arduino envía a la consola. ¿Por qué salen esos valores?

- Al no estar el A5 conectado a ninguna referencia válida, está flotando y los valores que captura son muestra de esa incoherencia. En realidad lo que está haciendo tu Arduino es captar ruido aleatorio de radiofrecuencia e intentar darle sentido, pero lo tiene mal, como podéis ver.
- No obstante en condiciones normales los valores que leerá serán relativamente bajos. ¿Quieres que las oscilaciones crezcan en valor? Fácil. Ponle una antena. Vale un simple cable de protoboard conectado desde el A5 a nada (O si agarras el otro extremo entre los dedos, _tú mismo harás de antena_).

## Un último comentario

Decíamos en una lección anterior, que la fidelidad con la que podemos muestrear una señal analógica dependía, básicamente, de la resolución de la muestra y de la velocidad a la que podíamos muestrear la señal (Sample Rate en inglés).

Ya dijimos que la familia Arduino, dispone de convertidores de 10 bits por lo que nuestra resolución es de 2^10 = 1.024 y en el caso del DUE de 2^12 = 4.096. Pero hasta ahora no hemos visto a qué velocidad podemos tomar muestras con nuestro Arduino. Lo comprobaremos, con este mismo circuito.

Tenemos una función llamada **millis()** que nos indica en milisegundos el tiempo transcurrido desde que iniciamos Arduino y la podemos usar para ver cuántas muestras podemos tomar por segundo.

```Arduino
/*
 * CARTROTECH  (https://cartrotech.github.io)
 * 
 * Projecto nº: ARD_05_02
 * Descripcion: Lectura de entradas analógicas
 * 
 * Fecha: 2025-04-25
 */

void setup()
{
    Serial.begin(9600);
}

void loop()
{
    unsigned long T;
    int n = 0;
    T = millis();
    while (millis() <= T + 1000) // Mientras no pase un Segundo = 1000 ms
    {
        analogRead(A5);
        n++; // Contamos cada vez que leemos
    }
    Serial.println(n);
}
```

- _Hemos usado un unsigned long para guardar millis porque es el tipo que Arduino usa internamente para su reloj. Sería un error manejar millis con un int porque su valor máximo es 32.767 y midiendo milisegundos el contador desbordaría en poco más de 32 segundos._

Si ejecutas este programa en un Arduino UNO te dará, más o menos, un resultado de 8.940 muestras o lecturas por segundo. No está mal.

Es adecuado para muestrear señales que no varían demasiado rápido con el tiempo, como son casi todos los sensores habituales en la industria, pero que se quedará corto si quieres muestrear señales de audio.

- _Para jugar con audio es mejor usar un Arduino DUE. Tiene una velocidad de reloj 4 veces más rápida (te hará falta), capacidad de muestreo a velocidad de audio (40 Khz) y auténticos convertidores DAC (digital to analog converters)._
- De hecho no es complicado aumentar la velocidad de muestreo hasta unas 20.000 muestras por segundo con un Arduino UNO, pero para esto tenemos que puentear Arduino y saltar a programar el chip interior Atmega 328. No es momento para esto, pero hay formas.

## Resumen de la lección

- Ya conocemos el uso del potenciómetro.
- Hemos presentado los conceptos básicos en la conversión analógica a digital.
- Aprendimos a leer las puertas analógicas de Arduino.
- Sabemos que podemos leer las puertas analógicas unas 8.900 veces por segundo con una resolución de 10 bits, es decir entre 0 y 1.024.
- Hemos conocido la función **millis()**.
