<template>
  <section class="src-components-formulario">

    <vue-form :state="formState" @submit.prevent="enviar()">
      <!--Campo de Entrada nombre entre 5 y 15 caracteres--> 
      <validate tag="div">
        <label for="nombre">Nombre</label>
        <input 
          id="nombre"
          type="text"
          v-model.trim="formData.nombre" 
          required
          autocomplete="off" 
          class="form-control"
          name="nombre" 
          minlength="5"
          maxlength="15"
        />
        <!--Mensajes de Validacion-->
        <field-messages name="nombre" show="$dirty">
          <div class="alert alert-info mt-1">OK</div>
          <div slot="required" class="alert alert-danger mt-1">El nombre es un campo requerido</div>
          <div slot="minlength" class="alert alert-danger mt-1">El nombre requiere como mínimo 5 caracteres</div>
        </field-messages>
      </validate>

      <!--Campo de Entrada  edad entre 18 y 120 años --> 
      <validate tag="div">
        <label for="edad">Edad</label>
        <input 
          id="edad"
          type="number"
          v-model.trim="formData.edad" 
          required 
          class="form-control"
          name="edad" 
          min="18"
          max="120"
        />
        <!--Mensajes de Validacion-->
        <field-messages name="edad" show="$dirty">
          <div class="alert alert-info mt-1">OK!</div>
          <div slot="required" class="alert alert-danger mt-1">La edad es un campo requerido</div>
          <div slot="min" class="alert alert-danger mt-1">El usuario no puede tener menos de 18 años</div>
          <div slot="max" class="alert alert-danger mt-1">El usuario no puede tener más de 120 años</div>
        </field-messages>
      </validate>

      <!--Campo de Entrada email válido---> 
      <validate tag="div">
        <label for="email">Email</label>
        <input 
          id="email"
          type="email"
          v-model.trim="formData.email" 
          required 
          class="form-control"
          name="email" 
        />
        <!--Mensajes de Validacion-->
        <field-messages name="email" show="$dirty">
          <div class="alert alert-info mt-1">OK!</div>
          <div slot="required" class="alert alert-danger mt-1">El email es un campo requerido</div>
          <div slot="email" class="alert alert-danger mt-1">El email debe tener un formato válido</div>
        </field-messages>
      </validate>
      <button :disabled="formState.$invalid" class="btn btn-primary my-3">Enviar</button>
    </vue-form>

    <hr>
    <div class="jumbotron bg-dark">
      <h5>INGRESOS</h5>
      <!--Representar en un tabla por debajo del mismo, en el mismo momento del ingreso -->
        <div>
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
        </div>
    </div>

    <hr>
    <div class="d-flex">
      <div class="jumbotron m-1 w-50 bg-dark " >
        <h5>DATOS</h5>
        <pre class="texto">{{ formData }}</pre>
      </div>
      <div class="jumbotron m-1 w-50 bg-dark">
        <h5>ESTADO</h5>
        <pre class="texto">{{ formState }}</pre>
      </div>
    </div>
  </section>
</template>

<script lang="js">

  export default  {
    name: 'src-components-formulario',
    props: [],
    mounted () {
    },
    data () {
      return {
        formState: {},
        formData: this.getInicialData(),
        usuarios: [{
          nombre: 'Germán Macchia',
          edad: '37',
          email: 'germanmacchia@gmail.com'
        }]
      }
    },
    methods: {
      getInicialData(){
        return{
          nombre: '',
          edad: '',
          email: ''
        }
      },
      enviar(){
        this.usuarios.push({...this.formData})
        this.formData = this.getInicialData()
        this.formState._reset()
      }
    },
    computed: {
      
    }
}


</script>

<style>
  .src-components-formulario {
    height: 100%;
    margin: 5vh 25vw 0 25vw;
  }

  .form-group{
    width: 50vw;
  }
  .texto{
    color: aliceblue;
  }

</style>
