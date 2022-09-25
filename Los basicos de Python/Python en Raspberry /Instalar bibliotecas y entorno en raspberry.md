
# Instalación de bibliotecas y entorno de trabajo de python en la raspbery pi 4

En python las bibliotecas tambien se les conoce como modulos, se pueden acceder a partes de las bibliotecas desde otros achivos para usarlos en el programa, esto facilita mucho el trabajo.

Raspberry Pi no tiene convertidor analogico digital y solo puede trabajar con sensores digitales.

Se va instalar biblioteca de comunicación I2C y para usar el sensor de tempetatura MLX90614.

1. Establecer comunicación desde Ubuntu con la Raspberry. 
    1. Conectar y encender la Raspberry 
    2. Comprobar que la configuración de raspberry tenga le Red y la contraseña de WiFi.

        * En mi caso tuve que reinstalar el sistema operativo a la tarjeta micro sd de la raspberry, desde la aplicación raspberry pi imagen cambie la configuración con los datos de la nueva red WiFi, cuidar el nombre de la raspberry y la contraseña asignada a la raspberry.

    3. Comprobar la IP asignada a la raspberry accediendo al modem o usando un detector de IP 
    4. Usar software VNC para conexion remota a raspberry 

2. Configurar la raspberry para aceptar la comunicación I2C
    1. Entrar a la configuración del equipo desde terminal en raspberry

            sudo raspi-config

        1. Interface options
            1. I2C
                1. Enable

3. Instalar modúlo para el sensor de temperatura MLX90614.
    1. En terminal usar:

           pip3 install PyMLX90614   
    2. Ir al sitio del proyecto para usar el [Sensor MLX90614](https://pypi.org/project/PyMLX90614/#files) y descargar el archivo.
    3. Extrer el archivo. 

            tar -xf PyMLX90614-0.0.4.tar.gz
    4. Colocarlo en directorio raiz.
    5. Configurar el paquete de comunicación y activar puerto de comunicación

            cd PyMLX90614-0.0.3 
            sudo apt-get install python-setuptools 
            sudo apt-get install -y i2c-tools 
            sudo python setup.py install 
            ls /dev/*i2c* 
            i2cdetect -y 1
    
4. Construir circuito. ![Circuito raspberry MLX90614](https://raw.githubusercontent.com/RamsesOrtiz36/Introduccion-a-Python/397480fa0b33f448aaa46d21cb85dd5d2a39a596/Los%20basicos%20de%20Python/Python%20en%20Raspberry/Circuito%20Raspberry%20sensor%20MLX90614.jpg).

5. Instalar entorno de trabajo IDLE, se cuenta con "Geany" de forma predeterminada pero se puede agregar el entorno IDLE.

        sudo apt-get install python3 
        sudo apt-get install idle3

6. Probar el entorno de trabajo, creamos un programa sencillo para acceder al sensor, el archivo se guarda con extención  **.py**

        #es código para python 3 
        from smbus2 import SMBus 
        from mlx90614 import MLX90614 
        bus = SMBus(1) 
        sensor = MLX90614(bus, address=0x5A) 
        print ("Temperatura ambiente :", sensor.get_amb_temp()) 
        print ("Temperatura de Persona u objeto :", sensor.get_obj_temp()) 
        bus.close()

+ Se actualizo el progrma desde la biblioteca, en el primer intento nos marcaba error de syntasix por **sensor.get_ambient()** y tambien en **sensor.get_object_1()**.

7. Resultados ![Captura de pantalla](https://github.com/RamsesOrtiz36/Introduccion-a-Python/blob/main/Los%20basicos%20de%20Python/Python%20en%20Raspberry/Resultados%20raspberry%20MLX90614%202022-09-24%20191740.png?raw=true)

El archivo se guarda en el escritorio y se puede ejecutar desde el entorno de trabajo con **F5** o desde terminal colocandose en el directorio guradado y ejecutando:

        python3 "Nombre_del_archivo" 
