<template>

  <section class="src-componentes-http-client">
    <div class="jumbotron">
      <h2>Componente HttpClient con mockapi</h2>
      <hr>
      <hr>
      <br>

      <button class="btn btn-dark my-3 mr-3" @click="getUsuariosXHRPromise()">XMLHttpRequest (Promise)</button> 
      <button class="btn btn-warning my-3 mr-3" @click="getUsuariosFetch()">Fetch</button>
      <button class="btn btn-success my-3 mr-3" @click="getUsuariosAxios()">Axios</button>
 
      <button class="btn btn-danger my-3 mr-3" @click="usuarios = []">Limpiar</button>
      <br>

      <div v-if="usuarios.length" class="table-responsive">
        <table class="table table-dark">
          <tr>
            <th>id</th>
            <th>Nombre</th>
            <th>Email</th>
            <th>Telefono</th>

          </tr>
          <tr v-for="usuario in usuarios" :key="usuario.id">
            <td>{{ usuario.id }}</td>
            <td>{{ usuario.nombre }}</td>
            <td>{{ usuario.email }}</td>
            <td>{{ usuario.numeroTel }}</td>

          </tr>
        </table>
      </div>
      <h4 v-else class="alert alert-danger text-center">No se encuentran datos</h4>
      
    </div>
  </section>

</template>

<script>

  export default  {
    name: 'src-componentes-http-client',
    props: [],
    mounted () {

    },
    data () {
      return {
         url: 'https://63588a5ec26aac906f43e3f7.mockapi.io/usuarios',
        usuarios : [ ]
      }
    },
    methods: {
       

       async getUsuariosXHRPromise() {
      
          try {
            let respuesta = await this.xhrPromise()
            this.usuarios = respuesta
          }
          catch(error) {
            console.error(error)
          }
      },
      xhrPromise() {
     

        return new Promise((resolve,reject) => {
          const xhr = new XMLHttpRequest()
          xhr.open('get', this.url)
          xhr.addEventListener('load', () => {
            if(xhr.status == 200) {
              let respuesta = JSON.parse(xhr.response)
              resolve(respuesta)
            }
            else {
              reject(`Error http: ${xhr.status}`)
            }
          })
          xhr.send()
        })
      },
   
      async getUsuariosFetch() {
  
        try {
          let response = await fetch(this.url)
          console.log(response)
          let respuesta = await response.json()
          this.usuarios = respuesta
        }
        catch(error) {
          console.error(error)
        }
      },
      async getUsuariosAxios() {
  
        try {
          let respuesta = await this.axios(this.url)
          this.usuarios = respuesta.data
        }
        catch(error) { console.error(error) } 

      }

    },
    computed: {

    }
}


</script>

<style scoped lang="css">
  .src-componentes-http-client {

  }

  .jumbotron {
    background-color: rgb(63, 109, 98);
    color: white;
  }

  hr {
    background-color: #bbb;
  }

</style>
