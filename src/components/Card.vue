<template>
  <div class="conversor">
    <h2>{{ moedaA }} para {{ moedaB }}</h2>
    <input
      class="form"
      type="text"
      v-model="moedaA_value"
      v-bind:placeholder="moedaA"
    />
    <input
      class="btn"
      type="button"
      value="Converter"
      v-on:click.prevent="conv"
    />
    <h2>{{ simb }} {{ moedaB_value }}</h2>
    <span class="er" v-for="error in erros" :key="error">{{ error }}</span>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: ["moedaA", "moedaB", "simb"],
  data() {
    return {
      moedaA_value: "",
      moedaB_value: 0,
      erros: []
    };
  },
  methods: {
    conv() {
      this.erros = [];
      this.moedaB_value = 0;
      if (!this.moedaA_value) {
        this.erros.push("Não há valores à converter!");
      } else if (isNaN(this.moedaA_value)) {
        this.erros.push("Letras não são números!");
      } else {
        let de_para = this.moedaA + "_" + this.moedaB;

        let url =
          "https://free.currencyconverterapi.com/api/v5/convert?q=" +
          de_para +
          "&compact=y";
        fetch(url)
          .then(res => {
            return res.json();
          })
          .then(json => {
            let cotacao = json[de_para].val;
            this.moedaB_value = (
              cotacao * parseFloat(this.moedaA_value)
            ).toFixed(2);
          });
      }
    }
  }
};
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.conversor {
  max-width: 300px;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.3);
  margin: 10px 15px;
  padding: 8px 4px;
  border-radius: 8px;
  background-color: #8092a3;
}
.form {
  font-weight: 300;
  margin: 4px;
  height: 25px;
  border: none;
  border-radius: 10px;
  background-color: #ffffff;
}
.btn {
  color: #ffffff;
  font-weight: 700;
  background-color: #327ddf;
  margin: 4px;
  border-radius: 4px;
  height: 25px;
  border: none;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
  box-sizing: border-box;
}
.er {
  color: #fa1b4b;
  font-weight: 600;
}
</style>
