<template>
  <div>
    <b-sidebar id="sidebar-right" title="Dodaj nowy produkt" right shadow>
      <div class="px-3 py-2">
        <form @submit="addProduct">
          <b-form-input
            type="text"
            v-model="name"
            name="name"
            placeholder="Dodaj produkt..."
            maxlength=30
            required
          ></b-form-input>
          <b-form-input
            type="number"
            v-model="cena"
            name="cena"
            placeholder="Cena"
            min="10"
            max="500"
            required
          ></b-form-input>
          <b-form-input
            type="text"
            v-model="opis"
            name="opis"
            maxlength=180
            placeholder="Opis"
            required
          ></b-form-input>
          <b-form-input
            type="text"
            v-model="firma"
            maxlength=20
            name="firma"
            placeholder="Firma"
            required
          ></b-form-input>
          <b-form-input
            type="text"
            v-model="model"
            maxlength=15
            name="model"
            placeholder="Model"
            required
          ></b-form-input>
          <b-form-input
            type="text"
            v-model="tag"
            maxlength=20
            name="tag"
            placeholder="Tag"
            required
          ></b-form-input>
          <b-form-input
            type="text"
            v-model="image"
            name="image"
            placeholder="Adres URL zdjęcia"
            required
          ></b-form-input>
          <input type="submit" value="Zapisz" class="btn" />
        </form>
      </div>
    </b-sidebar>
  </div>
</template>
<script>
//import uuid from 'uuid';

export default {
  name: "AddProduct",
  data() {
    return {
      name: "",
      cena: Number,
      opis: "",
      firma: "",
      model: "",
      tag: "",
      image: "",
      dostepny: "",
    };
  },
  methods: {
    addProduct(e) {
      e.preventDefault();
      const newProduct = {
        id: Math.ceil(Math.random() * 100),
        name: this.name,
        cena: this.cena,
        opis: this.opis,
        firma: this.firma,
        model: this.model,
        tag: this.tag,
        image: this.image,
        dostepny: true,
      };
      this.$emit("add-product", newProduct);

      this.name = "";
      this.cena = "";
      this.opis = "";
      this.firma = "";
      this.model = "";
      this.tag = "";
      this.image = "";
    },
  },
};
</script>
<style scoped>
.btn {
  color: rgb(19, 103, 160);
}
</style>