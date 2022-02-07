<template>
  <div id="formulario-persona">
    <form @submit.prevent="enviarFormulario">
      <div class="container">
        <div class="row">
          <div class="col-md-4">
            <div class="form-group">
              <label>Jugador</label>

              <input
                v-model="persona.nombre"
                type="text"
                class="form-control"
                :class="{ 'is-invalid': procesando && nombreInvalido }"
                @focus="resetEstado"
              />
            </div>
          </div>

          <div class="col-md-4">
            <div class="form-group">
              <label>Equipo</label>

              <input
                v-model="persona.equipo"
                type="text"
                class="form-control"
                :class="{ 'is-invalid': procesando && equipoInvalido }"
                @focus="resetEstado"
              />
            </div>
          </div>

          <div class="col-md-4">
            <div class="form-group">
              <label>Correo</label>

              <input
                v-model="persona.correo"
                type="email"
                class="form-control"
                :class="{ 'is-invalid': procesando && correoInvalido }"
                @focus="resetEstado"
              />
            </div>
          </div>
        </div>

        <div class="row">
          <div class="col-md-4">
            <div class="form-group">
              <button class="btn btn-primary">Añadir persona</button>
            </div>
          </div>
        </div>
      </div>

      <div class="container">
        <div class="row">
          <div class="col-md-12">
            <div
              v-if="error && procesando"
              class="alert alert -danger"
              role="alert"
            >
              Debes rellenar todos los campos!
            </div>

            <div v-if="correcto" class="alert alert-success" r ole="alert">
              La persona ha sido agregada correctamente!
            </div>
          </div>
        </div>
      </div>
    </form>
  </div>
</template>

<script>
export default {
    props:{
        personas:Array
    },
  name: "formulario-persona",
  data() {
    return {
      procesando: false,
      correcto: false,
      error: false,
      persona: {
        nombre: "",
        equipo: "",
        correo: "",
      },
    };
  },

  methods: {
    enviarFormulario() {
      this.procesando = true;

      this.resetEstado();

      // Comprobamos la presencia de errores

      if (this.nombreInvalido || this.equipoInvalido || this.correoInvalido) {
        this.error = true;

        return;
      }

      this.$emit("add-persona", this.persona);

      this.error = false;
      this.correcto = true;
      this.procesando = false;

      // Restablecemos el valor de la variables
      this.persona = {
        nombre: "",
        equipo: "",
        correo: "",
      };
    },

    resetEstado() {
      this.correcto = false;
      this.error = false;
    },
  },
};
</script>

<style scoped>
form {
  margin-bottom: 2rem;
}
</style>
