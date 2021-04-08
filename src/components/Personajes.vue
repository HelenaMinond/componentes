<template>
  <div>
    <!-- Formato utilizando botón para mostrar la información-->
    <!-- 
    <button @click="obtenerPersonajes()">Obtener Personajes</button>
    <div class="contenido" v-for="(person, index) in arrPersonajes" :key="index">
      <img v-bind:src="person.image" alt="Imagen Personaje" />
      <h2>{{ person.name }}</h2>
    </div>-->

    <!-- Formato sin utilizar botón para mostrar la información-->
    <div class="funcion">{{obtenerPersonajes()}}</div>
    <div class="contenido" v-for="(person, index) in arrPersonajes" :key="index">
      <img v-bind:src="person.image" alt="Imagen Personaje" />
      <h2>{{ person.name }}</h2>
    </div>
    
  </div>
</template>

<script>
export default {
  name: "Personajes",
  data() {
    return {
      arrPersonajes: [],
    };
  },

  methods: {
    async obtenerPersonajes() {
      const url = "https://rickandmortyapi.com/api/character";
      try {
        const req = await fetch(url);
        const reqJson = await req.json();
        //console.log(reqJson.results);
        this.arrPersonajes = reqJson.results;
        //console.log(this.arrPersonajes);
      } catch (error) {
        console.log(error);
      }
    },
  },
};
</script>

<style lang="scss">
.funcion {
  color: white;
  display: none;
}
.contenido {
  color: green;
  display: flex;
  flex-direction: row;
  align-items: center;
}

img {
  width: 120px;
  height: 120px;
  border-radius: 50%;
  margin: 0.5rem;
}

/*
button {
  position: fixed;
  right: 0;
  margin: 2rem;
  border: solid 2px green;
  border-radius: 5px;
  color: green;
  background-color: black;
  font-size: large;
}

button:hover {
  border: solid 4px green;
}
*/
</style>
