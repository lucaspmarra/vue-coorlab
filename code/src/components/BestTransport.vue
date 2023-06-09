<template>
  <div class="container">
    <b-navbar class="navbar" toggleable="lg" type="dark" variant="info">
      <b-navbar-brand class="ml-2">
        <b class="ml-2"><b-icon icon="truck"></b-icon> {{ appName }}</b>
      </b-navbar-brand>
    </b-navbar>
    <ContentBox :data="options" />

  </div>
</template>

<script>
import { BNavbar, BNavbarBrand } from 'bootstrap-vue'
import axios from 'axios'
import ContentBox from './ContentBox.vue'

export default {
  components: {
    BNavbar,
    BNavbarBrand,
    ContentBox,
  },
  data () {
    return {
      appName: 'Melhor Frete',
      options: [],
      selectedCity: null,
    }
  },
  methods: {
    async getAPI () {
      try {
        const response = await axios.get('http://localhost:3000/transport')
        this.options = response.data;
      } catch (error) {
        console.error(error)
      }
    },
    async fetchTransportData (city) {
      try {
        const response = await axios.get('http://localhost:3000/transport');
        const filteredOptions = response.data.filter((option) => option.city === city);
        console.log(`Dados de transporte para: ${city}`, filteredOptions);
      } catch (error) {
        console.error(error);
      }
    },
  },
  created () {
    this.getAPI()
  },
}
</script>

<style scoped>
.title .navbar {
  background-color: #00aca6 !important;
  padding: 2rem;
}


.title .navbar-brand,
b {
  margin-left: 20px;

}

.container {
  background: #00aca6;
  padding: 2rem;
  margin-top: 2rem;
  box-shadow: 0px 0px 5px 3px rgba(0, 0, 0, 0.75);
}
</style>
