# Mémo WebGL

*par flashjaysan*

## Création du contexte

Créez un fichier HTML basique et chargez le script JavaScript qui se chargera de gérer le canevas avec un contexte WebGL. L'attribut `defer` indique que le script ne s'exécutera qu'une fois l'intégralité du fichier HTML est chargé. Cela permet au script d'accéder à tous les éléments existants dans le fichier HTML.

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Contexte WebGL</title>
    <script src="main.js" defer></script>
  </head>
  <body>
    <p>Texte basique pour vérifier que la page s'affiche bien.</p>
    <canvas></canvas>
  </body>
</html>
```

Créez un fichier JavaScript (ici `main.js`) puis stockez dans une variable l'élément `canvas`.


```js
const canvas = document.querySelector('canvas');
```

Stockez dans une variable le contexte `webgl` du canevas.

```js
const gl = canvas.getContext('webgl');
```

**Remarque :** Passer à la méthode `getContext` l'argument `2d` pour un contexte 2D, `webgl` pour un contexte WebGL 1 ou `webgl2` pour un contexte WebGL 2.

Vérifiez que le contexte existe bien.

```js
if (gl === null)
{
  throw new Error('WebGL n\'est pas pris en charge.');
}
```

La programmation de WebGL se fait en plusieurs étapes.

- Créez les vertices dans une structure de données (niveau CPU).
- Créez un tampon dans le GPU.
- Chargez les vertices dans le tampon du GPU.
- Créez un vertex shader.
- Créez un fragment shader.
- Créez un programme.
- Attachez les deux shaders à ce programme.
- Liez le programme au GPU.
- Activez les attributs des vertices.
- Affichez le tout à l'écran.

Créez un tableau contenant les coordonnées des vertices.

```js
const vertexData = [
  0, 1, 0,
  1, -1, 0,
  -1, -1, 0
];
```

Créez le tampon et liez le au contexte en tant que tampon tableau.

```js
const buffer = gl.createBuffer();
gl.bindBuffer(gl.ARRAY_BUFFER, buffer);
```

Associez le tampon au tableau de vertices converti en tableau de type Float32. Comme les vertices ne vont pas changer, précisez que le tampon est statique (pour des vertices susceptibles d'être modifiés, passez l'argument `gl.DYNAMIC_DRAW`).

```js
gl.bufferData(gl.ARRAY_BUFFER, new Float32Array(vertexData), gl.STATIC_DRAW);
```

Créez le vertex shader.

```js
const vertexShader = gl.createShader(gl.VERTEX_SHADER);
gl.shaderSource(vertexShader, '

attribute vec3 position;

void main() {
  gl_Position = vec4(position, 1);
}

');
gl.compileShader(vertexShader);
```

Créez le fragment shader.

```js
const fragmentShader = gl.createShader(gl.FRAGMENT_SHADER);
gl.shaderSource(fragmentShader, '

void main() {
  gl_FragColor = vec4(1, 0, 0, 1);
}

');
gl.compileShader(fragmentShader);
```

Créez le programme.

```js
const program = gl.createProgram();
```

Attachez les shaders au programme.

```js
gl.attachShader(program, vertexShader);
gl.attachShader(program, fragmentShader);
```

Liez le programme au GPU.

```js
gl.linkProgram(program);
```

Récupérez l'index que WebGL a automatiquement donné à l'attribut `position` du programme.

```js
const positionLocation = gl.getAttribLocation(program, 'position');
```

Activez l'attribut pour qu'il puisse être utilisé.

```js
gl.enableAttribVertexArray(positionLocation);
```

Précisez la manière dont l'attribut doit être obtenu depuis le tampon.

```js
// passez l'index de l'attribut, le nombre d'éléments à récupérer dans le tampon, le type des éléments, false, 0, 0
gl.vertexAttribPointer(positionLocation, 3, gl.FLOAT, false, 0, 0);
```

Transférez le programme vers le GPU.

```js
gl.useProgram(program);
```

Affichez un triangle à partir des vertices.

```js
// passez le type de forme à construire, l'index du premier élément à utiliser et le nombre de vertices à utiliser
gl.drawArrays(gl.TRIANGLES, 0, 3);
```


