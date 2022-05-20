<template lang="html">

  <section class="src-components-pedidos">

    <div class="d-grid gap-2 col-6 mx-auto">
      <button class="btn btn-info m-3" type="button">XMLHttpRequest</button>
      <button class="btn btn-success m-3" type="button">Fetch</button>
      <button class="btn btn-primary m-3" type="button">Axios</button>
    </div>

    <table class="table table-dark">
        <tr>
            <th>Nombre</th>
            <th>Edad</th>
            <th>Email</th>
        </tr>
        <tr v-for="(usuario,index) in usuarios" :key="index">
            <td>{{ usuario.nombre }}</td>
            <td>{{ usuario.edad }}</td>
            <td>{{ usuario.email }}</td>
        </tr>
    </table>

  </section>

</template>

<script lang="js">

  export default  {
    name: 'src-components-pedidos',
    props: [],
    mounted () {

    },
    data () {
      return {

      }
    },
    methods: {

    },
    computed: {

    }
}


</script>

<style>
  .src-components-pedidos {
    height: 100vh;

  }
</style>
