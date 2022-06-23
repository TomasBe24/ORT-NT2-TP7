<template>

  <section class="src-components-users-comp">

    <div class="jumbotron">
    
      <h1>Usuarios</h1>

      <div v-if="usuarios.length" class="table-responsive">
        <table class="table table-dark">
          <tr>
            <th>Nombre</th>
            <th>Edad</th>
            <th>Email</th>
          </tr>
          <tr v-for="(usuario, index) in usuarios" :key="index">
            <td> {{ usuario.nombre }} </td>
            <td> {{ usuario.edad }} </td>
            <td> {{ usuario.email }} </td>
          </tr>
        </table>
      </div>
        <h5 v-else class="alert alert-danger">
          No se encontraron usuarios
        </h5>
    
    </div>

  </section>

</template>

<script>

  export default  {
    name: 'src-components-users-comp',
    props: [],
    created () {
      this.getUsuarios()

    },
    data () {
      return {
        url: 'https://628c22f5a3fd714fd02d3e5b.mockapi.io/usuarios',
        usuarios: []
      }
    },
    methods: {
      async getUsuarios(){
        try{
          let { data } = await this.axios(this.url)
          this.usuarios = data
        }
        catch(error){
          console.error('Error Axios', error);
        }
      }

    },
    computed: {

    }
}


</script>

<style scoped lang="css">
  
</style>
