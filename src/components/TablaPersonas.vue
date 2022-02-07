<template>
    <h3>Tabla de jugadores</h3>

    <table class="table">
        <thead>
            <tr>
            <th scope="col">id</th>
            <th scope="col">Jugador</th>
            <th scope="col">Equipo</th>
            <th scope="col">Correo</th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="persona in personas" :key="persona.id">
            <th scope="row">{{persona.id}}</th>
            <td>{{persona.nombre}}</td>
            <td>{{persona.equipo}}</td>
            <td>@{{persona.correo}}</td>
            </tr>
        </tbody>
    </table>
</template>

<script>
export default {
    props:{
        personas:Array
    }
    
}
</script>

<style scoped>

</style>