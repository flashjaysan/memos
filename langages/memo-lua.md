# Mémo Lua

par *flashjaysan*

## Les tables

Lua ne propose qu'une seule structure de donnée appelée *table*. Celle-ci peut être utilisée de bien des manières et fournit de puissantes possibilités. Cela peut cependant provoquer une confusion dans l'esprit d'un débutant.

### Utiliser une table comme une structure de donnée

```lua
local structure = {}
structure.element_x = valeur_a
structure.element_y = valeur_b
structure.element_z = valeur_c
```

Vous pouvez également utiliser la notation entre crochets (moins pratique et source de confusion si vous n'êtes pas habitué aux tableaux) :

```lua
local structure = {}
structure["element_x"] = valeur_a
structure["element_y"] = valeur_b
structure["element_z"] = valeur_c
```

La notation `une_table["cle"]` est donc équivalente à `une_table.cle` dans le cas de clé ne commençant pas par un chiffre.

Vous pouvez également initialiser directement la table lors de sa création :

```lua
local structure = {element_x = valeur_a, element_y = valeur_b, element_z = valeur_c}
```

**Attention !** Pensez bien à donner un nom à chaque élément de la table et à l'initialiser avec une valeur. Si vous ne précisez pas de nom d'élément, vous créerez un tableau.

Pour accéder au contenu d'un élément de la table, utilisez le nom de la variable suivi d'un point et du nom de l'élément.

```lua
tableau.element_y == valeur_b
```

### Utiliser une table comme un tableau

En Lua, les tables peuvent être utilisées comme des tableaux.

```lua
local tableau = {}
tableau[1] = valeur_a
tableau[2] = valeur_b
tableau[3] = valeur_c
tableau[4] = valeur_d
```

Vous pouvez également initialiser directement la table lors de sa création :

```lua
local tableau = {valeur_a, valeur_b, valeur_c, valeur_d}
```

**Remarque :** En Lua, le premier élément d'un tableau porte l'indice `1` et non `0`.

Pour connaitre la taille du tableau, utilisez le signe `#` devant le nom de la variable.

```lua
#tableau == 4
```

Pour accéder au contenu d'une case du tableau, utilisez le nom de la variable suivi de l'indice (entre crochets) de l'élément du tableau.

```lua
tableau[2] == valeur_b
```

**Attention :** Une table peut à la fois contenir des éléments représentés sous forme de tableau et des éléments représentés sous forme de structure de données. Vous pouvez même associer des fonctions aux éléments d'une table. Soyez donc prudent et raisonnable lorsque vous utilisez les tables. Je vous conseille de ne pas mélanger les types d'éléments et d'utiliser soit une table en tant que tableau soit en tant que structure de donnée tant que vous n'êtes pas sûr de vous.

```lua
local tableau = {}
tableau[1] = valeur_a
tableau[2] = valeur_b
tableau[3] = valeur_c
tableau[4] = valeur_d
tableau.element_x = valeur_e
tableau.element_y = valeur_f
tableau.element_z = valeur_g
tableau.affiche_bonjour = function ()
  print("Bonjour.")
end
```

En réalité, une table est une structure de donnée qui associe une *valeur* à une *clé*. Une clé est soit une suite de chiffres (dans ce cas, la clé s'utilise telle quelle sans guillemets) soit un identificateur complexe (une suite de chiffres, de lettres et du signe `_`) qui ne doit pas commencer par un chiffre (la clé s'utilise entre guillemets si vous utilisez la syntaxe entre crochets ou telle quelle si vous utilisez la syntaxe à point). Le code suivant est donc équivalent au précédent :

```lua
local tableau = {}
tableau[1] = valeur_a
tableau[2] = valeur_b
tableau[3] = valeur_c
tableau[4] = valeur_d
tableau["element_x"] = valeur_e
tableau["element_y"] = valeur_f
tableau["element_z"] = valeur_g
tableau["affiche_bonjour"] = function ()
  print("Bonjour.")
end
```

### Utiliser une table comme un tableau à deux dimensions

Pour bien comprendre les tableaux à deux dimensions, nous allons voir trois façons différentes de définir un tableau à deux dimensions. Chaque méthode donne le même résultat. Un tableau à deux dimensions est simplement un tableau contenant lui-même des tableaux.

- Vous pouvez définir une table contenant elle-même une liste de tables initialisées avec des éléments.

```lua
local tableau_2d = {
    {valeur_a, valeur_b, valeur_c},
    {valeur_d, valeur_e, valeur_f},
    {valeur_g, valeur_h, valeur_i},
    {valeur_j, valeur_k, valeur_l}
}
```

- Vous pouvez également définir une table vide pour représenter un tableau englobant. Créez ensuite une table initialisée avec des élements pour chaque case du tableau englobant.

```lua
local tableau_2d = {}
tableau_2d[1] = {valeur_a, valeur_b, valeur_c}
tableau_2d[2] = {valeur_d, valeur_e, valeur_f}
tableau_2d[3] = {valeur_g, valeur_h, valeur_i}
tableau_2d[4] = {valeur_j, valeur_k, valeur_l}
```

- Enfin, vous pouvez définir une table vide pour représenter un tableau englobant. Puis associer à chaque case de ce tableau une table vide pour représenter un tableau interne. Et enfin affecter une valeur à chaque case de chaque tableau interne.

```lua
local tableau_2d = {}
tableau_2d[1] = {}
tableau_2d[1][1] = valeur_a
tableau_2d[1][2] = valeur_b
tableau_2d[1][3] = valeur_c
tableau_2d[2] = {}
tableau_2d[2][1] = valeur_d
tableau_2d[2][2] = valeur_e
tableau_2d[2][3] = valeur_f
tableau_2d[3] = {}
tableau_2d[3][1] = valeur_g
tableau_2d[3][2] = valeur_h
tableau_2d[3][3] = valeur_i
tableau_2d[4] = {}
tableau_2d[4][1] = valeur_j
tableau_2d[4][2] = valeur_k
tableau_2d[4][3] = valeur_l
```

Pour connaitre la taille du tableau englobant, utilisez le signe `#` devant le nom de la variable.

```lua
#tableau_2d == 4
```

Pour connaître la taille d'un tableau interne, utilisez le sign `#` devant le nom de la variable suivi de l'indice (entre crochets) du tableau interne.

```lua
#tableau_2d[2] == 3
```

Pour accéder au contenu d'une case du tableau, utilisez le nom de la variable suivi de l'indice (entre crochets) du tableau interne et de l'indice (entre crochets) de l'élément du tableau interne.

```lua
tableau_2d[2][3] == valeur_f
```

### Les tables sont des références

Vous devez absolument garder à l'esprit que, contrairement aux types de base de Lua, les tables sont des références.

Si vous affectez à une nouvelle variable une table existante, cette dernière n'est pas copiée. En réalité, vous donnez à la nouvelle variable une référence à la table d'origine.

```lua
local point = {x = 30, y = 70} -- Création d'une table point.
local nouveau_point = point -- Affectation à nouveau_point de la référence à la table point.
nouveau_point.x = 10 -- Modification de l'élément x de nouveau_point
point.x ~= 30 -- mais cela se répercute sur point.
```

Si vous passez une table à une fonction, la fonction ne prend pas une copie de la table mais travail sur une référence à la table. Si vous modifiez la table dans la fonction, c'est la table d'origine que vous modifiez.

```lua
local point = {x = 30, y = 70} -- Création d'une table point.

function change_x(some_point)
  some_point.x = 10 -- Modifie l'élément x de la table point.
end
```

Pour résoudre ce genre de problème, il faut copier en profondeur les tables lorsque vous souhaitez vraiment créer une nouvelle copie. Consultez le [wiki de Lua](http://lua-users.org/wiki/CopyTable) pour plus d'informations.

### Parcours de tableau à une dimension

Un tableau peut être parcouru avec une boucle en utilisant l'indice pour accéder à un élément et le signe `#` pour obtenir le nombre d'éléments. Le plus simple est d'utiliser une boucle *pour* si vous souhaitez parcourir l'intégralité du tableau.

```lua
for i = 1, #tableau do
  -- Utilisez tableau[i] pour manipuler l'élément à la position i du tableau.
end
```

Ce qui peut également se traduire avec une boucle *tant que*.

```lua
local i = 1
while i <= #tableau do
  -- Utilisez tableau[i] pour manipuler l'élément à la position i du tableau.
  i = i + 1
end
```

Mais le réel intérêt d'une boucle *tant que* réside dans sa posibilité de sortir de la boucle avant la fin. Supposons, par exemple, que vous souhaitiez rechercher un élément particulier dans un tableau. Avec une boucle *pour*, vous devrez parcourir tout le tableau même si l'élément recherché est le premier.

```lua
local indice_element_recherche = 0
for i = 1, #tableau do
  if tableau[i] == valeur then
    indice_element_recherche = i
  end
end
-- Ici, indice_element_recherche a l'indice de la position de l'élément recherché ou 0 si on n'a pas trouvé d'élément égal à valeur.
```

**Remarque :** Le code précédent trouve l'indice du dernier élément égal à valeur si le tableau possède plusieurs éléments répondant à cette condition.

Avec une boucle *tant que*, vous pouvez ajouter une condition de sortie supplémentaire.

```lua
local element_trouve = false
local indice = 1
while indice <= #tableau and not element_trouve do
  if tableau[i] == valeur then
    element_trouve = true
  else
    indice = indice + 1
  end
end
-- Ici, si element_trouve est vrai, indice est égal à la position de l'élément recherché. Sinon, indice vaut un de plus que le nombre d'éléments du tableau.
```

**Attention !** Placez bien l'instruction `indice = indice + 1` dans le bloc `else` ou l'indice sera incrémenté même si l'élément est trouvé. A la sortie de boucle, l'indice vaudra un de plus que l'index de l'élément recherché.

De même, si vous souhaitez ajouter ou supprimer un élément dans un tableau, vous allez modifier le nombre d'élément. L'utilisation du signe `#` devient donc plus compliqué. Pour résoudre ce problème, la solution est de supprimer l'élément en dehors d'une boucle.

Ne faites surtout pas :

```lua
for i = 1, #tableau do
  if tableau[i] == valeur then
    table.remove(tableau, i) -- Vous supprimez l'élément mais vous modifiez également le nombre d'élément alors que vous continuez de parcourir le tableau.
  end
end
```

ou

```lua
local element_trouve = false
local indice = 1
while indice <= #tableau and not element_trouve do
  if tableau[i] == valeur then
    element_trouve = true
    table.remove(tableau, i) -- Vous supprimez l'élément mais vous modifiez également le nombre d'élément. Cependant, au prochain tour de boucle, grace à element_trouve, vous allez sortir de la boucle.
  else
    indice = indice + 1
  end
end
```

Utilisez plutôt les formes suivantes :

```lua
local indice_element_recherche = 0
for i = 1, #tableau do
  if tableau[i] == valeur then
    indice_element_recherche = i
  end
end
if indice_element_recherche ~= 0 then
  table.remove(tableau, indice_element_recherche)
end
```

ou

```lua
local element_trouve = false
local indice = 1
while indice <= #tableau and not element_trouve do
  if tableau[i] == valeur then
    element_trouve = true
  else
    indice = indice + 1
  end
end
if element_trouve then
  table.remove(tableau, indice)
end
```

Une autre forme de boucle `for` est disponible. Elle associe à chaque élément d'une table, son index, qu'il soit numérique ou alphanumérique.

```lua
for key, value in pairs(ma_table) do
  
end
```

### Parcours de tableau à deux dimensions

Pour parcourir un tableau à deux dimensions, souvenez-vous que c'est en réalité un tableau contenant d'autres tableaux. Vous pouvez donc parcourir le tableau général comme dans la section précédente.

```lua
for i = 1, #tableau_2d do
  -- Utilisez tableau_2d[i] pour manipuler le sous-tableau d'indice i du tableau général.
end
```

Vous pouvez ensuite accéder à chaque élément contenu dans les sous-tableaux avec une seconde boucle.

```lua
for i = 1, #tableau_2d do
  for j = 1, #tableau_2d[i] do
    -- Utilisez tableau_2d[i][j] pour manipuler l'élément à la position j du sous-tableau tableau[i].
  end
end
```

#### Les tableaux et les tilemaps

Une tilemap représentée sous la forme d'un tableau à deux dimensions est utilisée de manière à ce que sa lecture sous forme de code représente la disposition des tuiles dans un jeu.

```lua
local tilemap = {
  {tuile_a, tuile_b, tuile_c},
  {tuile_d, tuile_e, tuile_f},
  {tuile_g, tuile_h, tuile_i},
  {tuile_j, tuile_k, tuile_l}
}
```

Mais vous devez toujours garder à l'esprit que :

- Le premier indice de ce tableau correspond à un sous-tableau et donc à une ligne de la tilemap.
- Le second indice correspond à un élément d'un des sous-tableaux et donc à une colonne.

```lua
tilemap[2][1] == tuile_d -- Deuxième case vers le bas, première case vers la droite.
```

Tout cela pour bien vous faire prendre conscience que lorsque vous souhaitez parcourir le tableau, la boucle extérieur utilise un indice représentant les lignes (soit l'axe y) et la boucle intérieur utilise un indice représenant les colonnes (soit l'axe x). Souvenez-vous donc bien de ce détail lorsque vous travaillez avec une tilemap car l'ordre des indices est inversé (d'abord y puis x) par rapport à votre utilisation habituelle des coordonnées (d'abord x puis y).
