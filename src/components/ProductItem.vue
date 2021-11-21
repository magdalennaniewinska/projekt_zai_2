<template>
  <div
    class="product-item"
    v-bind:class="{ 'isnt-avaiable': !product.dostepny }"
  >
    <div class="container">
      <b-card
        v-bind:class="{ 'isnt-avaiable': !product.dostepny }"
        v-bind:title="product.name"
        v-bind:sub-title="product.cena" 
        v-bind:img-src="product.image"
        img-alt="Image"
        img-left
        tag="article"
        style="max-width: 20rem"
        class="mb-2"
      >
        <b-card-text>
          {{ product.opis }}
          <br />
          Producent: {{ product.firma }}
          <br />
          Model: {{ product.model }}
          <br />
          <b-button
            @click="$emit('filter-tag', product.tag)"
            variant="outline-secondary"
            >{{ product.tag }}
          </b-button>
        </b-card-text>
      </b-card>

        <div class="form-group row">
          <div class="col-md-3">
            <b-button
              @click="$emit('del-product', product.id)"
              variant="danger"
              class="text-center"
              >Usuń</b-button
            >
          </div>
          <div class="col-md-3">
            <b-button
              @click="$emit('open-edit', product.id)"
              variant="primary"
              class="text-center"
              >Edytuj</b-button
            >
          </div>
        </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ProductItem",
  props: ["product"],
};
</script>

<style scoped>
.product-item {
  background: #f4f4f4;
  padding: 10px;
  align-items: center;
}

.isnt-avaiable {
  text-decoration: line-through;
}

.container {
  align-items: left;
  padding: 10px;
  width: 310px;
  width: 300px;
}
.card-img-left {

  width: 300px;
  height: 300px;
  background: #f4f4f4;
}
.card-text {

  width: 300px;
}
</style>