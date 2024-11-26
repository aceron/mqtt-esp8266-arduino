# mqtt-esp8266-arduino

## Requisitos de instalación:

1.	Mosquitto Broker (MQTT): https://mosquitto.org/download/

2.	Python 3.10 o superior (Opcional: se recomienda utilizar MiniConda o algún otro gestor de entornos virtuales): https://docs.anaconda.com/miniconda/install/ 

3.	Utilizando Pip, instalar las siguientes librerías (Opcional: si se tiene MiniConda, primero hay que abrir “Anaconda Prompt” en Windows, o ejecutar el comando "conda activate" en sistemas Unix):

```
pip install mysql-connector-python
pip install paho-mqtt
```

## Configuración:

1.	Ubicar el archivo de configuración de Mosquitto:

    a.	Para Windows, generalmente se ubica en “C:\Program Files\mosquitto\mosquitto.conf”

    b.	Para sistemas Unix (e.g. MacOS o Ubuntu), podemos localizar la dirección con el siguiente comando: which mosquitto

2.	Editar el archivo de configuración de Mosquitto:

    a. Abrir el archivo “mosquitto.conf” con algún editor de texto simple en modo administrador (e.g. Notepad, Notepad++, VSCode, etc… No utilizar Word, LibreOffice, o algún editor de texto enriquecido).

    b. Agregar las siguientes 2 líneas de texto al archivo y guarde los cambios:
```
listener 1883
allow_anonymous true
```

3.	Ejecutar el Mosquitto Broker

    a.	Usualmente, el instalador habilita al Broker como servicio por defecto. Primero hay que deshabilitarlo. En Windows: Buscar en la barra de inicio “Services”, luego seleccionar “Mosquitto Broker”, y finalmente seleccionar “Stop”.	En Unix (MacOS o Ubuntu): Correr el comando “pkill -9 mosquitto” en modo administrador.

    b.	Abrir la terminal de comandos, dirigirse a la carpeta de instalación de Mosquitto, y correr el siguiente comando:
  	
```
mosquitto -v -c mosquitto.conf
```

4. Al ejecutarse, debe aparecer un mensaje indicando que el Broker se encuentra activo.

## Puesta en marcha:

1.	Descargar el siguiente repositorio para Arduino: https://github.com/luisllamasbinaburo/ESP8266-Examples/tree/master/12%20-%20ESP8266%20y%20MQTT/35_Mqtt 

2.	Además de instalar las herramientas necesarias para el microcontrolador respectivo (e.g. ESP8266), es necesario instalar la librería “PubSubClient” de “Nick O’Learly” en el gestor de librerías del Arduino IDE.

3.	Seguir las instrucciones para ejecutar el ejemplo https://www.luisllamas.es/como-usar-mqtt-en-el-esp8266-esp32/ 

4.	El Mosquitto Broker (MQTT) estará disponible en el puerto 1883 de la computadora principal. Es necesario configurar los Arduinos para que encuentren el servicio en ese puerto, además de dirigirlos a la dirección IP de la computadora que se encuentre corriendo el Broker.

5.	Se comparte en este repositorio un código de ejemplo para hacer una conexión desde un Arduino por MQTT, hasta una base de datos en MySQL utilizando Python.

rev. 2024.11.26 by aceron
