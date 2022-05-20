<template>
  <section class="src-components-navbar">
    <h1>TP4: Vue CLI - Router / Formularios</h1>
    <ul class="nav nav-tabs navbar-dark bg-dark">
      <li class="nav-item">
        <router-link to="/">
          <a class="nav-link" href="#">Formulario</a>
        </router-link>
      </li>
      <li class="nav-item">
        <router-link to="/Pedidos">
          <a class="nav-link" href="#">Pedidos</a>
        </router-link>
      </li>
    </ul>
  </section>
</template>

<script>

  export default  {
    name: 'src-components-navbar',
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
  h1{
    padding: 4vh;
  }
  a{
    color: greenyellow !important;
  }
</style>
