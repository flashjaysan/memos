# Mémo Turtle

par *flashjaysan*

## Installation

Le module `turtle` est normalement préinstallé avec Python. Vous n'avez pas besoin d'installer de package.

## Utilisation

Pour utiliser le module `turtle`, commencez par l'importer dans votre programme.

```python
import turtle
turtle.title('titre') # modifie le titre de la fenêtre
turtle.mode('logo')
turtle.speed(vitesse) # 0 à 10
```

### L'objet Screen

```python
screen = turtle.Screen()
screen.canvwidth = 640
screen.canvheight = 360
screen.exitonclick()
```

### L'objet Turtle

```python
new_turtle = turtle.Turtle()
new_turtle.shape('turtle') # arrow, circle, square, triangle, turtle, classic
new_turtle.shapesize(longueur, largeur, contour)
new_turtle.color('coral')
new_turtle.forward(distance)
new_turtle.backward(distance)
new_turtle.turn_right(angle)
new_turtle.turn_left(angle)
new_turtle.home() # revient à la position 0, 0 tourné vers le nord
new_turtle.goto(x, y)
new_turtle.set_heading(angle) # 0 = nord, 90 = est, 180 = sud, 270 = ouest
x, y = new_turtle.pos() # renvoie un tuple de la position de la tortue
new_turtle.circle(rayon) # dessine un cercle. Le rayon peut être négatif
new_turtle.dot(rayon) # dessine un cercle plein
```

La couleur du stylo définit la couleur des lignes.
La couleur de la tortue définit la couleur de remplissage.

```python
turtle.begin_fill() # Use this command before you start drawing the shape you want to be filled
turtle.end_fill() # Use this command when you have finished drawing the shape to be filled.
turtle.pendown() # Put the pen down to draw
turtle.penup() # ‘Lift’ the pen from the screen
turtle.pensize(integer) # Set the size of the pen to the given integer.
turtle.pencolor(string) # Set the pen colour to the string given. Note the American spelling.
turtle.fillcolor(string) # Set the fill colour to the string given. See list of colours below.
turtle.bgcolor(couleur)
turtle.color(string) # Set both the fill colour and pen colour to given string.
turtle.color(string1, string2) # Set the pen and fill colour at the same time. String1 should be the name of the pen colour, and string2 is the fill colour.
```

```python
turtle.stamp() # Stamp the current turtle shape onto the screen. 
turtle.clearstamps() # Clear all of the stamps on the screen.
stampID = turtle.stamp() # Stamps the turtle onto the screen, and sets the variable stampID to an integer, unique to each stamp.
turtle.clearstamp(stampID) # Clear the stamp with the given stampIDnumber.
```

Annuler la dernière commande

```python
t.undo()
```

Effacer tous les dessins d'une tortue

```python
t.clear()
```

Effacer l'écran

```python
t.reset()
```

Laisser un tampon de la forme de la tortue

```python
id_tampon = t.stamp()
```

Effacer un tampon

```python
t.clearstamp(id_tampon)
```

Cloner une tortue

```python
nouvelle_tortue = t.clone()
```

La nouvelle tortue possède les mêmes propriétés que la tortue d'origine.

Changer le mode des couleurs

Par défaut, le mode de couleurs définit chaque composante comme une valeur comprise entre 0 et 1. Vous pouvez modifier ce mode pour des valeurs comprises entre 0 et 255.

```python
turtle.colormode(0.1) # défaut
turtle.colormode(255)
```

Générer une couleur aléatoire

```python
def random_color():
    turtle.colormode(255)
    r = random.randint(0, 255)
    g = random.randint(0, 255)
    b = random.randint(0, 255)
    return (r, g, b)
```
