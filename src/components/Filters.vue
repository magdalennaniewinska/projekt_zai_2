<template>
  <div>
    <b-sidebar id="sidebar-1" title="Filtruj i sortuj produkty" shadow>
      <div class="px-3 py-2">
        <form @submit="applyPrice">
      <span>Filtruj po cenie:</span>
      <b-form-input
        type="number"
        v-model="cenaMIN"
        name="cenaMIN"
        placeholder="MIN"
        min=0
        max=500
        step=10
        required></b-form-input>
      <b-form-input
        type="number"
        v-model="cenaMAX"
        name="cenaMAX"
        placeholder="MAX"
        min=0
        max=500
        step=10
        required></b-form-input>
      <input type="submit" value="Filtruj" class="btn" />
    </form>
      </div>
      <div class="px-3 py-2">
    <b-form-group label="Sortuj produkty:" v-slot="{ ariaDescribedby }">
        <form @submit="applySorting">
      <b-form-checkbox-group
        id="checkbox-group-2"
        v-model="selected"
        :aria-describedby="ariaDescribedby"
        name="flavour-2"
      >
        <b-form-checkbox value="cena" v-model="sorting" :disabled="sorting.includes('name')" > Po cenie</b-form-checkbox>
        <b-form-checkbox value="name" v-model="sorting" :disabled="sorting.includes('cena')"> Według nazwy</b-form-checkbox>
      </b-form-checkbox-group>
      <input type="submit" value="Sortuj" class="btn" />
        </form>
    </b-form-group>
  </div>
  <div class="px-3 py-2">
    <b-form-group label="Pokaz:" v-slot="{ ariaDescribedby }">
        <form @submit="applyAvailable">
      <b-form-checkbox-group
        id="checkbox-group-2"
        v-model="selected"
        :aria-describedby="ariaDescribedby"
        name="flavour-2"
      >
        <b-form-checkbox value="1" v-model="available"> Tylko dostępne produkty</b-form-checkbox>
      </b-form-checkbox-group>
      <input type="submit" value="Zapisz" class="btn" />
        </form>
    </b-form-group>
  </div>
    </b-sidebar>
  </div>
</template>
  <!-- <div class="row">
    
  </div> -->

<script>
export default {
  name: "Filters",
  data() {
    return {
      cenaMIN: Number,
      cenaMAX: Number,
      selectedFilter: "",
      sorting: [],
      available: [],
    };
  },
  methods: {

    applyPrice(e) {
       e.preventDefault();
       this.$emit('apply-price', this.cenaMIN, this.cenaMAX) 
    },
    applySorting(e) {
       e.preventDefault();
       this.$emit('apply-sorting', this.sorting) 
    },
    applyAvailable(e) {
       e.preventDefault();
       this.$emit('apply-available', this.available) 
    }
  },
};
</script>

<style scoped>
.row {
  background: #333;
  color: #fff;
  text-align: center;
  padding: 10px;
}
.btn {
  color: rgb(19, 103, 160)
}
</style>