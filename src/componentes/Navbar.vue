<template>

  <section class="src-componentes-navbar">
      <nav class="navbar navbar-expand-md navbar-dark bg-dark">

        <router-link to="/formulario-av">
          <a class="navbar-brand" href="#">Inicio</a>
        </router-link>
        
        <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>

        <div class="collapse navbar-collapse" id="navbarNav">
          <ul class="navbar-nav">

             
            <li class="nav-item">
              <router-link to="/formulario-av">
                <a class="nav-link" href="#">FormularioAv</a>
              </router-link>
            </li>

            <li class="nav-item">
              <router-link to="/http-client">
                <a class="nav-link" href="#">HttpClient</a>
              </router-link>
            </li>            
             
          </ul>
        </div>
      </nav>
  </section>

</template>

<script>

  export default  {
    name: 'src-componentes-navbar',
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

<style scoped lang="css">
  .src-componentes-navbar {

  }
</style>
