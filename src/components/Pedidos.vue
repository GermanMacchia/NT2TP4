<template lang="html">

  <section class="src-components-pedidos">

    <div class="d-grid gap-2 col-6 mx-auto">
      <button class="btn btn-info m-3" v-on:click="getPostXHR()" type="button">XMLHttpRequest</button>
      <button class="btn btn-success m-3" @click="getPostFetch()" type="button">Fetch</button>
      <button class="btn btn-primary m-3" @click="getPostAxios()" type="button">Axios</button>
      <button class="btn btn-danger m-3" v-on:click="posts=[]" type="button">Reset</button>
    </div>
    <div v-if="posts.length" class="table-responsive border border-5 border-white mx-auto h-50 w-75"> 
      <table class="table table-dark ">
          <tr>
              <th class="text-success">Id</th>
              <th class="text-success">Nombre</th>
              <th class="text-success">Email</th>
              <th class="text-success">Numero Telefono</th>
          </tr>
          <tr v-for="(post) in posts" :key="post.id">
              <td>{{post.id}}</td>
              <td>{{post.nombre}}</td>
              <td>{{post.email}}</td>
              <td>{{post.tel}}</td>
          </tr>
      </table>
    </div>
    <h4 v-else class="alert alert-danger mx-auto w-75">No hay posts disponibles</h4>
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
        url: 'https://628822847af826e39e5d1d18.mockapi.io/usuarios',
        posts: []
      }
    },
    methods: {
      getPostXHR(){
        const xhr = new XMLHttpRequest()
        xhr.open('get', this.url)
        xhr.addEventListener('load', () => {
          if(xhr.status == 200){
            let respuesta = JSON.parse(xhr.response)
            this.posts = [...respuesta]
          }
          else{
            console.error('Error XHR', xhr.status)
          }
        })
        xhr.send()
      },
      getPostFetch(){
        fetch(this.url)
          .then(respuesta => respuesta.json())
          .then(respuesta => this.posts = [...respuesta]) 
          .catch( error => console.error('Error fetch', error)) 
      },
      getPostAxios(){
        this.axios(this.url)
          .then( respuesta => {
              let { data: datos } = respuesta;
              this.posts = datos 
            })
          .catch( error => console.error('Error axios', error))
      }
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
