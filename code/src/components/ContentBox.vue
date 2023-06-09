<template>
  <div class="content">
    <div class="form">
      <b-form>
        <h1><i></i>Insira o destino e o peso</h1>
        <b-form-group class="w-100" id="destino" label="Destino">
          <b-form-select class="w-100" v-model="selected" :options="data">
          </b-form-select>
        </b-form-group>
        <b-form-group id="peso" label="Peso">
          <b-form-input class="md-6" placeholder="Peso da carga em kg"></b-form-input>
        </b-form-group>
      <b-form-group><b-button class="botao" type="submit" variant="primary">Analisar</b-button></b-form-group>
      </b-form>
    </div>
    <div class="result">result</div>
  </div>
</template>

<script>
  export default {

    props:{
      data:{
        type: Array,
        required: true,
      }
    },

    data(){
      return{
        selected: "null",
        options: [
          { value: null, text: 'Selecione o destino', disabled: true}

        ]
      }
    }
  }
</script>

<style scoped>

.content{
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
.botao{
  margin-top: 2rem;
  justify-content: center;
}

</style>