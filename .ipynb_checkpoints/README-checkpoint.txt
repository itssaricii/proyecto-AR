### CONFIGURACIÓN DEL GITHIB ###
Para clonar el repo:
En SageMaker ir a Git->Clone Git Repostory->https://github.com/itssaricii/proyecto-AR

Para subir cambios:
git add -u (añade todos los cambios de los ficheros )
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