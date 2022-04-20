# BASE DE DATOS CON MONGODB 
## Caso práctico: Recetas de cocina

NOMBRE: Felipe Bascuñán Morales
CARRERA: Ingeniería Informática 
ASIGNATURA: Bases de datos no estructuradas
PROFESOR: Alberto Marambio Riveros
FECHA: 18 de abril de 2022

# Introducción

En este documento se describirá las consideraciones tomadas para un caso práctico de creación de base de datos no relacional con el motor MongoDB. 

# Caso propuesto
## Diagrama

El siguiente esquema entidad-relación se usará de base para la creación de la base de datos.

![diagrama](/diagrama.png)

## Entidades

    • Recipes
    • Recipe_Category
    • Recipes_Steps
    • Recipe_Step_Ingredients
    • Ingredient_Types
    • Ingredients

# Interpretación

Dado que los nombres de las entidades son lo suficientemente descriptivos se procede a detallar la interpretación de cada entidad para su implementación en MongoDB

**Recipes**: Receta, pertenece a una categoría está compuesta de pasos que a su vez contienen ingredientes.
**Recipe_Category**: Entidad que representa a las categorías a la cual pertece cada receta, en categoría no debiera necesitarse la información completa de la receta pero si el identificador de cada una de ellas.
**Recipe_Steps**: Pasos, pertenece a receta y contiene principalmente ingredientes e instrucciones.
**Ingredients**: Entidad que debe pertenecer a Recipe_Steps y puede contener Ingredients_Types.
**Ingredients_Types**: representa una forma de categorizar ingredientes por su tip.
**Recipe_Step_Ingredients**: Relación entre los pasos para la receta (Recipe_Steps) y los ingredientes (Ingredients).

> Se permitirá cierta redundancia de datos, lo cual facilitará el desarrollo de consultas. Se simplificará el esquema debido a que existen entidades fuertemente relacionadas.
> Se tiene que los pasos para cada receta (Recipe_Steps) siempre estarán ligados a la receta (Recipes) por lo tanto Recipe contendrá Recipe_Steps. A su vez Recipe_Steps contendrá ingredientes. 
> Recipe_Steps no tiene sentido que exista sin su receta por lo tanto se asume que no será usual consultar Recipe_Steps de forma independiente. Por ello no se creará una colección que la represente por si sola.
> Se considerará Ingredient_Types como parte de la colección Ingredients. Siendo así puede haber muchos tipos de ingredientes y cada ingrediente pertenecerá a un solo tipo, con lo cual se mantiene la relación 1 a muchos.
