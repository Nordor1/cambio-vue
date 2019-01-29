<template>
  <div class="card">
    <H1>Conversor de moedas.</H1>
    <div class="row">
      <Card moeda-a="USD" moeda-b="BRL" simb="R$"></Card>
      <Card moeda-a="BRL" moeda-b="USD" simb="US$"></Card>
    </div>
    <div class="row">
      <Card moeda-a="EUR" moeda-b="BRL" simb="R$"></Card>
      <Card moeda-a="BRL" moeda-b="EUR" simb="EUR"></Card>
    </div>
    <div class="row">
      <Card moeda-a="CAD" moeda-b="BRL" simb="R$"></Card>
      <Card moeda-a="BRL" moeda-b="CAD" simb="CAD"></Card>
    </div>
  </div>
</template>

<script>
import Card from "./components/Card.vue";

export default {
  name: "card",
  components: {
    Card
  }
};
</script>

<style>
body {
  background-color: #aebdce;
}
.card {
  margin: auto;
  max-width: 900px;
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.row {
  border-bottom: solid rgb(156, 156, 156);
  display: flex;
  justify-content: space-around;
  margin-top: 30px;
}
</style>
