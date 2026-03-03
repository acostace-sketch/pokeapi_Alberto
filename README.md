# Proyecto: Mini Pokédex con PokeAPI

## 1. Introducción
Este proyecto consiste en una aplicación web sencilla que consume datos de la API externa **PokeAPI** para mostrar información sobre los Pokémon iniciales de la primera generación. 

La aplicación cuenta con 3 botones, uno para cada pokemon inicial, al pusar el botón correpondiente se muestra la información de cada pokemon.

Al cargar la web se carga el pokemon Bulvasur para mostrar algo por defecto al iniciar la página.


## 2. Explicación del Código Principal

### Consumo de API (Fetch)
Se ha utilizado la función fetch() para la obtención de los datos. Adicionalmente he implementado la función await que espera a la llegada de los datos para que el codigo posteriormente implementado implementado en esa función no se ejecute hasta tener los datos y la pagina pueda funcionar correctamente.

### Endpoints
Los endpòints de este proyecto són las URL que apuntan a los datos del pokemon que queremos acceder, estos són los que he usado para este caso.
* `https://pokeapi.co/api/v2/pokemon/bulbasaur`
* `https://pokeapi.co/api/v2/pokemon/charmander`
* `https://pokeapi.co/api/v2/pokemon/squirtle`

### Información mostrada
Cada vez que se recibe la respuesta JSON de la API, el script:
1. Limpia los contenedores anteriores (mediante `innerHTML = ""`) para evitar que las habilidades se acumulen.
2. Crea nuevos elementos de lista (`<li>`).
3. Actualiza el atributo `src` de la imagen para mostrar el sprite correspondiente del pokemon seleccionado.

## 3. Catch error
Se ha implementado un catch error por si algo sale mal durante la petición de los datos por el motivo que fuese.



