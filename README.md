# Ensayos Humedades de Suelo.

### **Índice**
1. [Tabla de distribución de sensores.](#id1)
2. [Configuración de direcciones SDI12 para Teros11.](#id2)
3. [Alimentación y cableado.](#id3)
4. [Descarga de datos.](#id4)
5. [Verificar valores instantáneos de variables.](#id5)

<div id='id1' />

## 1. Tabla de distribución de sensores.

A continuación, se despliegan los cuadros con la información de los sensores instalados.

**Tabla 1.** Estación Paso Alejo, Coihueco, en avellano europeo, variedad Barcelona. 
|**Tratamiento**|**Profundidad (cm)**|**N° serie sensor**|**Modelo sensor**|**N° de serie**|**Largo cable (m)**|**Canal CR300**|
|--|--|--|--|--|--|--|
|T1|20|1|T10|47976|20|SE1 ???|
|T1|40|2|T10|47977|20|SE2 ???|
|T1|60|3|T10|45893|20|SE3 ???|
|T2|20|1|T10|48400|10|SE4|
|T2|40|2|T10|47979|10|SE5|
|T2|60|3|T10|49020|10|SE6|
|T3|20|1|T11|14624|40|C1-0|
|T3|40|2|T11|14622|40|C1-1|
|T3|60|3|T11|14627|40|C1-2|
|T4|20|1|T11|20596|10|C2-0|
|T4|40|2|T11|20530|10|C2-1|
|T4|60|3|T11|20533|10|C2-2|


**Tabla 2.** Estación Paso Alejo, Coihueco, en avellano europeo, variedad Lewis. 
|**Tratamiento**|**Profundidad (cm)**|**N° serie sensor**|**Modelo sensor**|**N° de serie**|**Largo cable (m)**|**Canal CR300**|
|--|--|--|--|--|--|--|
|T1|20|1|T10|33482|20|SE1|
|T1|40|2|T10|46622|20|SE2|
|T1|60|3|T10|46625|20|SE3|
|T2|20|1|T11|20532|10|C1-0|
|T2|40|2|T11|20316|10|C1-1|
|T2|60|3|T11|20311|10|C1-2|
|T3|20|1|T10|46626|20|SE4|
|T3|40|2|T10|46623|20|SE5|
|T3|60|3|T10|46627|20|SE6|
|T4|20|1|T11|20314|10|C2-0|
|T4|40|2|T11|20310|10|C2-1|
|T4|60|3|T11|20312|10|C2-2|

<div id='id2' />

## 2. Configuración de direcciones SDI12 para Teros11.

En el caso de tener múltiples sensores Teros11 o Teros12, se pueden configurar sus direcciones SDI12 para disponer de un máximo de 10 sensores por salida digital. En donde las direcciones de cada sensor deben ser configuradas desde 0 a 9 sin repetir por canal. En el caso del data CR300 se disponen de 2 canales digitales SDI12, C1 y C2, en el caso del data CR1000 se disponen de 4 canales SDI12, C1, C3, C5 y C7.
Para configurar la dirección SDI12 del sensor, hay que asegurar que exista conexión entre el data y el computador, luego se puede utilizar la aplicación Terminar Emulator (Emulador de Terminal) que en el software PC400 se encuentra en menú ***Datalogger->Terminar Emulator***. Una vez abierta la ventana de la terminal, hacer cliks sobre el botón ***Abrir la terminal***. Si todo sale bien, la terminal responderá con el modelo de datalogger, ejem:  ***CR300>***, luego se puede seguir la siguiente secuencia de comandos y respuestas, entre la terminal y el data:


```
CR300> SDI12    //Consuta para configurar protocolos SDI12.
1: C1
2: C2
Select SDI12 Port: 2    //Se debe seleccionar un puerto.
Entering SDI12 Terminal. Press ESC to exit  //Ingrese comando SDI12
?!  //Se consulta por la dirección actual del puerto seleccionado
0   //La dirección actual es cero.
0A2!    //Se configura una nueva dirección con el comando: "<dir actual>A<nueva dir>!", "A" en mayúscula.
?!  //Se verifica la nueva dirección
2   //Cnfirmado cambio de derección SDI12 del sensor.

```


A continuación se muestran los comandos en el emulador de terminal del software PC400.

![Figura 1](images/img01.png)

**Figura 1.** Emulador de terminal, PC400. 

<div id='id3' />

## 3. Alimentación y cableado.

* 1 Teros10 -> amperaje: ***12mA***, voltaje: ***3 a 15 Volts***
* 1 Teros11 -> amperaje: ***16mA***, voltaje: ***4 a 15 Volts***

Por otra parte tenemos que el Switch 12V del CR300 suministra en total 900mA.

A continuación se muestran el cableado para los sensores Teros10 y Teros11.

![Figura 2](images/img02.png)

**Figura 2.** Cableado sensor Teros10. 

![Figura 3](images/img03.png)

**Figura 3.** Cableado sensor Teros11.


<div id='id4' />

## 4. Descaraga de datos.

La descarga de datos se realiza con el programa PC400, para esto se debe acceder a la pestaña ***Collect Data***, seleccionar las tablas: …    , y luego presionar el botón …


<div id='id5' />

## 5. Verificar valores instantáneos de variables.

La verificación de las variables en tiempo real se realiza con el programa PC400, para esto se debe acceder a la pestaña ***Monitor Data***, luego presionar el botón ***Add***, se abrirá una nueva ventana, en donde se debe seleccionar el tipo de variable ***Public***. Para en el cuadro derecho seleccionar específicamente las variables que se requiere monitorear.
Es muy importante que el tipo de variable sea ***Public***, ya que estos valores se actualizan a cada 10 segundos. En la variable se identifica tanto el parámetro que miden, como el tratamiento, profundidad y variedad. A continuación, se presenta un cuadro resumen con las variables de acuerdo a las siglas con que comienzan.

**Tabla 3.** Cuador para verificar valores instantáneos de variables. 
|**Siglas**|**Parametro**|
|--|--|
|hs_|Humedad de suelo (Una por sensor teros10 y teros11)|
|ts_|Temperatura de suelos (Una por sensor teros 11)|
|mV_|Voltaje de salida (Una por sensor teros10 y teros11, en este caso, se recomienda no agragarlas)|