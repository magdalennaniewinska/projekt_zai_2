<template>
  <b-navbar toggleable type="dark" variant="dark">
    <b-button v-b-toggle.sidebar-1>Filtruj / Sortuj produkty</b-button>
    <b-navbar-brand href="/">Twój ulubiony sklep AGD</b-navbar-brand>
    <b-button v-b-toggle.sidebar-right>Dodaj produkt</b-button>
  </b-navbar>
</template>

<script>

export default {
  name: "Header",
};
</script>

<style scoped>
.header {
  background: #333;
  color: #fff;
  text-align: center;
  padding: 10px;
}
.header a {
  color: #fff;
  padding-right: 5px;
  text-decoration: none;
}
</style>