---
layout: post
title: "¿Qué es y qué partes tiene Arduino?"
date: 2025-04-15 21:26:43 +0200
categories: arduino básico
excerpt: "Introducción a Arduino: plataforma de prototipos electrónica de código abierto que conecta el mundo físico con el digital. Conoce sus principales partes y funcionamiento."
---

## ¿Qué es y qué partes tiene Arduino?

### Objetivos

- Presentar la placa Arduino  
- Saber cómo alimentarla  
- Diferenciar las distintas partes funcionales  
- Saber cómo funciona Arduino  

### ¿Qué es Arduino?

Arduino es una plataforma de prototipos electrónica de código abierto (open-source) basada en una sencilla placa con entradas y salidas, y un entorno de desarrollo basado en el lenguaje de programación Processing. Es un dispositivo que conecta el mundo físico con el virtual, o el mundo analógico con el digital.

![Pines del Arduino Uno](/assets/images/01-01-Arduino-UNO-pines.png)]

### Partes de un Arduino

El Arduino, como todo componente, está conformado por diferentes partes como entradas, salidas, alimentación, comunicación y *shields*.

#### Entradas

Son los pines de nuestra placa que podemos utilizar para hacer lecturas. En la placa Uno son los pines digitales (del 0 al 13) y los analógicos (del A0 al A5).

#### Salidas

Los pines de salida se utilizan para el envío de señales. En este caso, los pines de salida son únicamente los digitales (del 0 al 13).

#### Otros pines

También tenemos otros pines como los GND (tierra), 5V que proporciona 5 voltios, 3.3V que proporciona 3.3 voltios, los pines REF de referencia de voltaje, TX (transmisión) y RX (lectura) usados para comunicación serie, RESET para reiniciar, Vin para alimentar la placa y los pines ICSP para comunicación SPI.

#### Alimentación

Como hemos visto, el pin Vin sirve para alimentar la placa, pero lo más habitual es hacerlo mediante el conector de alimentación usando un voltaje de 7 a 12 voltios. También podemos alimentarla por el puerto USB, pero en la mayoría de aplicaciones no la tendremos conectada a un ordenador. (Ver anexo 1 para más información).

#### Comunicación

En nuestros tutoriales nos comunicaremos con Arduino mediante USB para cargar los programas o enviar/recibir datos. Sin embargo, no es la única forma de comunicación. Cuando insertamos una *shield*, esta se comunica con nuestra placa utilizando los pines ICSP (comunicación ISP), los pines 10 a 13 (también usados para comunicación ISP), los pines TX/RX o cualquier pin digital ya que pueden configurarse como entradas o salidas digitales para enviar o recibir pulsos.

#### Shields

Se denomina así a las placas que se insertan sobre Arduino a modo de escudo, ampliando sus posibilidades de uso. En el mercado existen infinidad de *shields* para cada tipo de Arduino. Algunas de las más comunes son las de Ethernet, Wi-Fi, ultrasonidos, pantallas LCD, relés, matrices de LEDs, GPS.

Arduino está constituido en el hardware por un microcontrolador principal llamado Atmel AVR de 8 bits (programable con un lenguaje de alto nivel), presente en la mayoría de los modelos de Arduino.

### Características generales de todas las placas Arduino

- Microprocesador ATmega328  
- Memoria Flash 32 KB (2 KB para el bootloader)  
- SRAM 1 KB  
- EEPROM 512 bytes  
- Microcontrolador ATmega328  
- Completamente autónomo: una vez programado no necesita estar conectado al PC  
- Velocidad de reloj: 16 MHz  
- 13 pines para entradas/salidas digitales (programables)  
- 5 pines para entradas analógicas  
- 6 pines para salidas analógicas (salidas PWM)  
- Voltaje de operación: 5V  
- Voltaje de entrada (recomendado): 7-12 V  
- Voltaje de entrada (límite): 6-20 V  
- Corriente DC por pin I/O: 40 mA  
- Corriente DC pin 3.3V: 50 mA  

### ¿Cómo funciona Arduino?

Arduino es una placa basada en un microcontrolador, específicamente un ATMEL. Un microcontrolador es un circuito integrado (podemos decir un microchip) en el cual se pueden grabar instrucciones. Estas instrucciones se escriben utilizando un lenguaje de programación que permite al usuario crear programas que interactúan con circuitos electrónicos.

Normalmente un microcontrolador posee entradas y salidas digitales, entradas y salidas analógicas y pines para protocolos de comunicación. Arduino es una placa que cuenta con todos los elementos necesarios para conectar periféricos a las entradas y salidas del microcontrolador. Se trata de una placa impresa con todos los componentes necesarios para el funcionamiento del microcontrolador y su comunicación con una computadora a través de comunicación serie.

La comunicación serie es un protocolo que antiguamente fue muy utilizado a través de los puertos serie que traían las computadoras antiguas.
