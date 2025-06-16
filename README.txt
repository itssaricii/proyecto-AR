### CONFIGURACIÓN DEL GITHIB ###
Para clonar el repo:
En SageMaker ir a Git->Clone Git Repostory->https://github.com/itssaricii/proyecto-AR

Para subir cambios:
git add -u (añade todos los cambios de los ficheros. Esto solo añade ficheros ya rastreados. Nosotros generamos nuevos archivos de pesos con los checkpoints --> Es más recomendable "git add .")
git add ruta/al/fichero (añadir un fichero que no esté todavía en git)
git commit -m "NOMBRE:comentarios" (para describir lo que hay en el commit)
git push (para subir cambios)
git pull (para recibir cambios)

Os pedirá usuario y contraseña al hacer push:
El usuario es el de vuestro github y la contraseña debeís crearla como token aquí:
https://github.com/settings/tokens
Importante coger opción Generate new token (classic)->y seleccionar repo mínimo

### CONFIGURACIÓN DEL ENTORNO EN SAGEMAKER ###
1. En un terminal de SageMaker crear nuevo virtual enviroment
conda create -n rl-env python=3.8 -y
conda activate rl-env

2. Instalar dependencias:
pip install tensorflow==2.5.3 keras-rl2==1.0.5
pip install gym==0.17.3
pip install git+https://github.com/Kojoley/atari-py.git
pip install pyglet==1.5.0
pip install Pillow==9.5.0
pip install h5py==3.1.0
pip install torch==1.9.0

3. Hacer que el venv esté disponible en Jupyter:
conda install ipykernel -y
python -m ipykernel install --user --name rl-env --display-name "Python (RL Env)"

4. Reiniciar el kernel en SageMaker y eligir: Python (RL Env) 
    # Sale a arriba a la derecha en la pestaña en la que se tiene abiertio el .ipynb

IMPORTANTE: Ejecutar en paralelo "upload_weights" para que se suban los pesos al repositorio. Ahora mismo está puesto a un checkeo cada minuto.

SUPER IMPORTANTE: No os fieis del tiempo de sagemaker y antes de que se os acabe el tiempo, cortad el kernel manualmente y subid los cambios a git, porque de lo contrario, perdeis todo el progreso.

### TRICKS PARA COLAB ###
Para que podáis dejar el colab entrenando y no os cierre la sesión por inactividad del navegador.
En Chrome:
1. Abrid el notebook en colab (Abrir--> Desde github)
2. Ctrl+Mayus+I para abrir las herramientas de desarrollador
3. En Consola abajo escribid 'allow pasting' y darle a enter
4. Pegad el siguiente javascript:

function ClickConnect() {
    var iconElement = document.getElementById("toggle-header-button");
    if (iconElement) {
        var clickEvent = new MouseEvent("click", {
            bubbles: true,
            cancelable: true,
            view: window
        });
        iconElement.dispatchEvent(clickEvent);
    }
}

setInterval(ClickConnect, 6000);

5. Veréis que cada 6 segundos la pantalla se desplaza abajo y arriba un poco alternativamente, 
esto debería ser suficiente para que Colab considere que estáis en la sesion aún.