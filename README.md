# EXPLICACIÓN DEL CODIGO

La logica de la página funciona mediante el siguiente codigo:

```html
<script>
        
        async function loadPokemon(nombre) {
            const url = `https://pokeapi.co/api/v2/pokemon/${nombre}`;

            try {
                
                const respuesta = await fetch(url);
                
                
                if (!respuesta.ok) throw new Error("No se encontró el Pokémon");

                const datos = await respuesta.json();

                
                document.getElementById('pokemon-name').textContent = datos.name.toUpperCase();
                document.getElementById('pokemon-sprite').src = datos.sprites.front_default;
                document.getElementById('pokemon-sprite').alt = `Imagen de ${datos.name}`;

                
                const listaTipos = document.getElementById('pokemon-types');
                listaTipos.innerHTML = ""; 
                datos.types.forEach(item => {
                    const li = document.createElement('li');
                    li.textContent = item.type.name;
                    listaTipos.appendChild(li);
                });

                
                const listaHabilidades = document.getElementById('pokemon-abilities');
                listaHabilidades.innerHTML = ""; 
                datos.abilities.forEach(item => {
                    const li = document.createElement('li');
                    li.textContent = item.ability.name;
                    listaHabilidades.appendChild(li);
                });

            } catch (error) {
                console.error("Error al obtener datos:", error);
                alert("Hubo un error al conectar con la PokéAPI");
            }
        }

        
        window.onload = () => loadPokemon('bulbasaur');
    </script>


```



    1.- Primero lo que hacemos es definir lo que será nuestro endpoint, la url con el nombre del pokemon al que queremos acceder,
    al pulsar el botón del pokemon a mostrar, se obtiene su nombre y con ello el acceso a sus datos mediante la url.

    2.- Uso de Await para recibir el JSON con los datos para consiltarlos después -- Usamos await para que el resto del codigo de la función no se ejecute hasat obtener los datos necesarios para mostrar la información, ya que si no la applicación podria no funcionar de forma correcta.

    3.- Modificamos el nombre y imagen del pokemon, para ello accedemos a los elementos con getElementById y lo modificamos con la información obtenida para cada caso.

    4.-Para modificar la lista de tipos y habilidades, limpiamos la lista anteriormente mostrada al obtener un nuevo elemento con esta linea de codigo -- listaTipos.innerHTML = ""; -- posteriormente con uin bucle foreach mostramos en forma de lista cada habilidad y cada tipo que tiene ese pokemon en cuestión.

    5.- Se ha utilizado un try / catch por si el acceso a datos falla por algún motivo, en caso de que falle se mosttrará un error.

    6.- Usamos la función window.onload para que cuando la ventana se abra muestr el pokemon bulvasur llamando a la función que acabamos de crear. De esta forma no se mostrarán los mensajes por defecto y hace la página más presentable.



