<template>
  <div id="app" class="container">
    <div class="row">
      <div class="col-md-12">
        <h1>Personas</h1>
      </div>
    </div>

    <div class="row">
      <div class="col-md-12">
        <formulario-persona @add-persona="agregarPersona" />

        <tabla-personas :personas="personas" />
      </div>
    </div>
  </div>
</template>

<script>
import TablaPersonas from "@/components/TablaPersonas.vue";
import FormularioPersona from "@/components/FormularioPersona.vue";

export default {
  name: "app",
  components: {
    TablaPersonas,
    FormularioPersona,
  },
  data() {
    return {
      personas: [
        {
          id: "100",
          nombre: "Michael Jordan",
          equipo: "Chicago bulls",
          correo: "michael@gmail.com",
        },
        {
          id: "200",
          nombre: "Bryan Scott",
          equipo: "LA Lakers",
          correo: "bryan@gmail.com",
        },
        {
          id: "300",
          nombre: "Kevin Mchale",
          equipo: "Celtics Boston",
          correo: "kevin@gmail.com",
        },
      ], //cierra array personas
    }; //cierra return
  }, //cierra data
  methods: {
    agregarPersona(persona) {
      let id = 0;
      if (this.personas.length > 0) {
        id = this.personas[this.personas.length - 1].id + 1;
      }
      this.personas = [...this.personas, { ...persona, id }];
    },

    enviarFormulario() {
      this.$emit("add-persona", this.persona);
    },
  },

  computed: {
    nombreInvalido() {
      return this.persona.nombre.length < 1;
    },

    equipoInvalido() {
      return this.persona.equipo.length < 1;
    },

    correoInvalido() {
      return this.persona.correo.length < 1;
    },
  },
};
</script>

<!--
<template>
  <HelloWorld msg="Mitos de la NBA" autor="Adaya" />
  <tabla-personas v-bind:personas="personas" />
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import TablaPersonas from "./components/TablaPersonas.vue";

export default {
  name: "App",
  components: {
    HelloWorld,
    TablaPersonas,
  },
  data() {
    return {
      personas: [
        {
          id: "100",
          nombre: "Michael Jordan",
          equipo: "Chicago bulls",
          correo: "michael@gmail.com",
        },
        {
          id: "200",
          nombre: "Bryan Scott",
          equipo: "LA Lakers",
          correo: "bryan@gmail.com",
        },
        {
          id: "300",
          nombre: "Kevin Mchale",
          equipo: "Celtics Boston",
          correo: "kevin@gmail.com",
        },
      ], //cierra array personas
    }; //cierra return
  }, //cierra data
}; //cierra default
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
-->
