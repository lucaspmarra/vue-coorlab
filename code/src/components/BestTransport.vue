<template>
  <div class="container">
    <b-navbar class="navbar" toggleable="lg" type="dark" variant="info">
      <b-navbar-brand class="ml-2">
        <b class="ml-2"><b-icon icon="truck"></b-icon> {{ appName }}</b>
      </b-navbar-brand>
    </b-navbar>
    <ContentBox :data="transportData"/>
  </div>

</template>

<script>
import {
  BNavbar,
  BNavbarBrand,
} from 'bootstrap-vue'
import axios from 'axios'
import ContentBox from './ContentBox.vue'

export default {
  components: {
    BNavbar,
    BNavbarBrand,
    ContentBox,
  },
  data() {
    const appName = ''

    return {
      appName,
      transportData: null,
    }
  },
  created() {
    // Implemente aqui o GET dos dados da API REST
    // para que isso ocorra na inicialização da pagina
    this.getAPI()
    this.appName = 'Melhor Frete'
  },
  methods: {
    // Implemente aqui os metodos utilizados na pagina
    methodFoo() {
      console.log(this.appName)
    },
    getAPI(){
      axios.get('http://localhost:3000/transport').then(response => 
      this.transportData = response.data).catch(error => console.error(error))
    },
  },
}
</script>

<style scoped>
.title .navbar {
  background-color: #00aca6 !important;
  padding: 2rem;
}


.title .navbar-brand, b {
  margin-left: 20px;
  
}

.container {
  background: #00aca6;
  padding: 2rem;
  margin-top: 2rem;
  box-shadow: 0px 0px 5px 3px rgba(0,0,0,0.75);
}
</style>
