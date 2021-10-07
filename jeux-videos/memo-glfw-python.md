# Mémo GLFW Python

par *flashjaysan*

## Installation

Créez un environnement virtuel.

```
pip install glfw
```

## Premier programme

```python
import glfw

# initialisation de la bibliothèque. Nécessite d'appeler terminate ensuite.
if not glfw.init():
    raise Exception("glfw can not be initialized!")

# creation de la fenêtre
window = glfw.create_window(1280, 720, "My OpenGL window", None, None)

# vérification que la fenêtre est créée
if not window:
    glfw.terminate()
    raise Exception("glfw window can not be created!")

# make the context current
glfw.make_context_current(window)

# boucle de jeu
while not glfw.window_should_close(window):
    glfw.poll_events()#nécessaire pour que les évènements soient pris en compte
    glfw.swap_buffers(window)# échange les deux tampons vidéos

# libère la mémoire proprement. Complémente init.
glfw.terminate()
```