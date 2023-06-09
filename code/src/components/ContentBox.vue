<template>
  <div class="content">
    <div class="form">
      <b-form @submit.prevent="submitForm">
        <h1><i></i>Insira o destino e o peso</h1>
        <b-form-group class="w-100" id="destino" label="Destino">

          <b-form-select v-model="selected">
            <option v-for="city in uniqueCities" :key="city" :value="city">
              {{ city }}
            </option>
          </b-form-select>
        </b-form-group>

        <b-form-group id="peso" label="Peso">
          <b-form-input v-model="weight" class="md-6" placeholder="Peso da carga em kg"></b-form-input>
        </b-form-group>

        <b-form-group>
          <b-button class="botao" type="submit" variant="primary">Analisar</b-button>
        </b-form-group>
      </b-form>
    </div>

    <div class="result" v-if="selected">
      <h2>Cidade selecionada: {{ selected }}</h2>
      <div v-for="option in filteredOptions" :key="option.id">
        <h3>{{ option.name }}</h3>
        <p>Custo de Frete até 100Kg [R$/Kg]: {{ option.cost_transport_light }}</p>
        <p>Custo de Frete mais de 100Kg [R$/Kg]: {{ option.cost_transport_heavy }}</p>
        <p>Cidade de destino: {{ option.city }}</p>
        <p>Tempo de entrega: {{ option.lead_time }}</p>
      </div>
    </div>

  </div>
</template>

<script>

export default {
  props: {
    data: {
      type: Array,
      required: true,
    }
  },

  data () {
    return {
      selected: null,
      weight: null,
      result: null,
    };
  },
  computed: {
    uniqueCities () {
      return [...new Set(this.data.map((data) => data.city))];
    },
    filteredOptions () {
      return this.selected ? this.data.filter((data) => data.city === this.selected) : [];
    },
  },
/*   methods: {
    submitForm () {
      if (!this.selected || !this.weight) {
        alert('Por favor, selecione o destino e insira o peso.');
        return;
      }
    }
  }, */
  watch: {
    selectedCity (newCity) {
      console.log(`Cidade selecionada: ${newCity}`);
      this.fetchTransportData(newCity);
    },
  },
}
</script>

<style scoped>
.content {
  width: auto;
  display: flex;
  justify-content: space-between;
}

.form {
  width: 45%;
  height: 50vh;
  background-color: red;
  display: flex;
  justify-content: center;
  padding: 2rem;
}

.botao {
  margin-top: 2rem;
  justify-content: center;
}
</style>