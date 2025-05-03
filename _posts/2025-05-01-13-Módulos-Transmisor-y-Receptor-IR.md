---
layout: default
title: 13 - Módulos Transmisor y Receptor IR
date: 2025-05-03 10:00:00 +0200
categories: arduino sensores
excerpt: En este experimento, aprenderemos a utilizar el módulo transmisor
de infrarrojos y el receptor de infrarrojos.
---

## Finalidad

En este experimento, aprenderemos a utilizar el módulo transmisor
de infrarrojos y el receptor de infrarrojos.
De hecho, en nuestra vida cotidiana juegan un papel importante en la
mayoría de los electrodomésticos que se utilizan en este tipo de
dispositivos, como aire acondicionado, TV, DVD, etc. En realidad se basa
en su teledetección sin hilos y es muy conveniente utilizarlos.

## Material

| Imagen | Descripción |
| :---: | :---: |
| ![Imagen](/assets/images/material/mat_unor3.png) | Arduino Uno o compatible |
| ![Imagen](/assets/images/material/mat_cables.png) | Cables de conexión |
| ![Imagen](/assets/images/material/mat_KY022.png) | Módulo receptor IR KY022 |
| ![Imagen](/assets/images/material/mat_KY005.jpeg) | Módulo emisor IR KY005 |

## Descripción del material

### Receptor IR

Sensor de infrarrojos tipo 1838 para uso con señales IR de 38 KHz.

- Tensión de alimentación: 2,7 a 5,5 V
- Frecuencia: 37,9 KHz
- Alcance del receptor: 18 m (típico)
- Ángulo de recepción: 90 °

![Receptor IR](/assets/images/ard/ard_13_01.png)

Los detectores IR son pequeños microchips con fotorresistencia que se ajustan para
escuchar la luz infrarroja. Casi siempre se utilizan para la detección
de control remoto: cada reproductor de TV y DVD tiene uno en la parte
frontal para leer la señal IR desde el mando a distancia. En el interior del
mando a distancia hay un LED IR coincidente, que emite impulsos IR
para decir al televisor que se encienda, se apague o cambie de canal. La luz
IR no es visible al ojo humano, por lo que se necesita un poco más
de trabajo para probar una configuración.

Los detectores IR están filtrados especialmente para la luz infrarroja, no son
buenos para detectar la luz visible. Por otro lado, las fotorresistencias son
buenas para detectar la luz visible de color amarillo/verde, no son buenas
para la luz IR.

- Los detectores IR tienen un desmodulador en el interior que busca IR
  modulados a 38 kHz. No se detectará el brillo de un LED de IR, sino que
  tendrá que parpadear a 38 kHz. Las fotorresistencias no tienen ningún tipo de
  desmodulador y pueden detectar cualquier frecuencia (incluida la CC) dentro
  de la velocidad de respuesta de la fotorresistencia (que es de unos 1 kHz).
- Los detectores IR son de salida digital: si detectan una señal IR de
  38 kHz, dan una salida baja (0V) o si bien no detectan ninguna,
  producen una salida alta (5V). Las fotorresistencias actúan como
  resistencias, la resistencia cambia en función de la cantidad de luz a
  la que están expuestas.

### Transmisor IR

Este módulo se utiliza generalmente junto con el módulo de receptor
IR, las aplicaciones de este módulo son muy amplias en nuestra vida
común. El LED-IR se puede utilizar para construir una barrera de luz o un
transmisor de señal de control remoto IR.

Este módulo es igual que un LED, pero el color de la luz no se puede
ver al ojo humano, sino que puedes ver la luz a través de la cámara
del teléfono.

![Emisor IR](/assets/images/ard/ard_13_02.png)

## Montaje

Este montaje es muy sencillo, no necesitamos protoboard pero en
cambio necesitamos dos placas arduino.

Los cables de alimentación (5V y GND) tienen posiciones fijas en la placa,
los cables de datos los conectaremos en la entrada/salida correspondiente
según indicamos en el código

![Montaje receptor](/assets/images/ard/ard_13_03.png)
![Montaje emisor](/assets/images/ard/ard_13_05.png)

---

![Esquema eléctrico receptor](/assets/images/ard/ard_13_04.png)
![Esquema eléctrico emisor](/assets/images/ard/ard_13_06.png)

## Programación

```Arduino
/*
 * CARTROTECH  (https://cartrotech.github.io)
 * 
 * Projecto nº: ARD_13_IRe (subir a la placa del emisor)
 * Descripcion: En este experimento, aprenderemos a utilizar el módulo transmisor de infrarrojos y el receptor de infrarrojos.
 * 
 * Fecha: 2025-05-03
 */


#include <IRremote.h>

IRsend irsend;

void setup()
{

}

void loop()
{
    digitalWrite(13,LOW);
    irsend.sendRC5(0x0, 8); //enviar código 0x0 (8 bits)
    delay(200);
    digitalWrite(13,HIGH);
    irsend.sendRC5(0x1, 8);
    delay(200);
}

```

```Arduino

/*
 * CARTROTECH  (https://cartrotech.github.io)
 * 
 * Projecto nº: ARD_13_IRr (subir a la placa del receptor)
 * Descripcion: En este experimento, aprenderemos a utilizar el módulo transmisor de infrarrojos y el receptor de infrarrojos.
 * 
 * Fecha: 2025-05-03
 */

#include <IRremote.h>
#define RECV_PIN 11 //Pin de recepción de la señal IR
#define LED 13 //define LED pin

IRrecv irrecv(RECV_PIN); //crear el objeto irrecv para el receptor IR en el pin indicado

decode_results results; //declaramos la variable results (datos de la recepción)

void setup()
{
    pinMode(LED, OUTPUT); //inicializa LED como salida
    Serial.begin(9600);
    irrecv.enableIRIn(); //activa el objeto irrecv
}

void loop()
{
    if (irrecv.decode(&results)) //comprobamos si llegan datos
    {
        int state;
        if ( results.value == 1 )
        {
            state = HIGH;
        }
        else
        {
            state = LOW;
        }
    digitalWrite( LED, state );
    Serial.println(results.value);
    irrecv.resume(); // comenzamos una nueva recepción
    }
}

```

## Conceptos importantes

- Cómo funcionan el transmisor y el receptor de infrarrojos.
- Cómo se puede utilizar el módulo transmisor y el receptor de infrarrojos.
