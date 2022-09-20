# Introduccion-a-Python
Instalación de Python 3 en Ubuntu, Intalacion de Anaconda y Jupyter con las extenciones para Visual Studio Code (VSC) y la configuración del ambiente para programar en python

## Comprobar version de Python y primer programa.
Normalemente se tiene instalado Python junto con Ubuntu, pero por si acaso comprobamos la version del Python desde terminal en ubuntu

    python --version

El anterior es para comprobar version menor a 3, para ver si tiene Python3 usamos

    python3 --version
Ahora ya que vimos que version tenemos, ejecutamos un pequeño programa en python desde terminal, abrimos un editor de texto en terminal 

    nano hola.py
creando un archivo de python con nombre "hola", este archivo contiene la instrucción para escribir "Hola python" y nada más. la instruccion es:

    print("Hola python")
Para guardar el archivo usamo "Crtl+O" y cerramos archivo con "crtl+x", asi volvemos a la terminal normal, Si queremos ejecutar el archivo de python que acabamos de crear usamos 

    sudo python3 hola.py
Indicando que somos Super usuarios (sudo) el programa a usar (python3) y el archivo a ejecutar (hola.py)

## Instalacón de ambiente de trabajo en VSC con Anaconda y Jupyter
Este ambiente de trabajo contiene bibliotecas para usarse en los programas de python  pore ejemplo numpy y Pandas, Anacnoda se descarga desde https://www.anaconda.com/products/individual
Tener en cuenta el sistema operativo 

Una vez descargado se debe ejecutar.

    bash ~/Descargas/Anaconda3-2022.05-Linux-x86_64.sh

Cuidarse de poner bien la dirección, la version, el año.

Cuando se ejecuta el archivo aparece el contrato de aceptación, seguir las instrucciones al leerlo

### Lo siguiente es Jupyter que es una interfaz para trabajar con todo tipo de archivos como audio y video

    sudo apt-get install jupyter
Ademas se ocupa una extencion que permita trabajar con python y jupyter en VSC, para esto se recomiendan las extenciones:
* Python de inteliSense de Microsoft
* jupyter notebook suport de microsoft

## Configuración del ambiente de trabajo
Ya tenemos insytalados los programas y extenciones ahora falta configurarlos.

Para usar Python se escoge un interprete en VSC ir a:
 * Menu View
    
    * Command Palette

        "python:select interpreter"




