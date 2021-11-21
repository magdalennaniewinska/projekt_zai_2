<template>
  <div id="app">
    <Header />
    <AddProduct v-on:add-product="addProduct"/>
    <Filters v-on:apply-price="applyPrice" v-on:apply-sorting="applySorting" v-on:apply-available="applyAvailable"/>
    <Products v-bind:products="products" v-on:del-product="deleteProduct" v-on:filter-tag="filterTag" v-on:apply-price="applyPrice" v-on:apply-sorting="applySorting"  v-on:apply-available="applyAvailable"/>
  </div>
</template>

<script>
import Header from './components/layouts/Header';
import Products from './components/Products';
import AddProduct from './components/AddProduct';
import Filters from './components/Filters';

export default {
  name: 'App',
  components: {
    Header,
    Filters,
    AddProduct,
    Products,
  },
  data() {
    return {
      products: [
        {
          id: 0,
          name: "Lokówka",
          cena: 129,
          opis: "Klasyczna lokówka BaByliss 38 mm Curling Tong to idealne rozwiązanie dla miłośniczek luźnych fal.",
          firma: "BaByliss",
          model: "Curling Tong C453E",
          tag: "Uroda",
          image: "https://f01.esfr.pl/foto/4/49393220017/95d76dc04f9c540ee5270b46c244fe84/babyliss-bab-lokowka-25mm-c451e-wyl-,49393220017_8.jpg",
          dostepny: true
        },
        {
          id: 1,
          name: "Golarka",
          cena: 299,
          opis: "Golarka wyposażona w 3 ruchome ostrza adaptuje się do konturów twarzy i sprawia, że dokładne golenie jest łatwe. Szybkie i łatwe czyszczenie bez zdejmowania głowicy golącej.",
          firma: "Braun",
          model: "Series 5 50-R1000s",
          tag: "Uroda",
          image: "https://f00.esfr.pl/foto/3/64932076625/e83581467bba9f47bdc4cbc3029c034f/braun-series-5-50-r1000s,64932076625_8.jpg",
          dostepny: false
        },
        {
          id: 2,
          name: "Żelazko",
          cena: 349,
          opis: "Pionowy wyrzut pary, funkacja eco, system antywapienny. 15 programów prasowania dostosowanych do rónych materiałów.",
          firma: "Tefal",
          model: "FV6870",
          tag: "Prasowanie i szycie",
          image: "https://f00.esfr.pl/foto/6/80789918241/8cb1e57decb9f1ae55435703bd9950fd/tefal-smart-protect-plus-fv6870,80789918241_8.jpg",
          dostepny: true
        },
        {
          id: 3,
          name: "Parownica do ubrań",
          cena: 69.99,
          opis: "System duzej pary. Funkcje dodatkowe: ciągły strumień pary, odłączany zbiornik wody",
          firma: "Vesta",
          model: "EGS01",
          tag: "Prasowanie i szycie",
          image: "https://f00.esfr.pl/foto/1/40818384433/fbc903dc68f4d8674227841eb56b5817/vesta-parownica-do-ubran-egs01-vesta,40818384433_8.jpg",
          dostepny: true
        },
        {
          id: 4,
          name: "Suszarka",
          cena: 179.99,
          opis: "Suszarka Remington Curl & Straight Confidence to kompletny zestaw do profesjonalnej stylizacji włosów każdej długości – zarówno kręconych, jak i prostych.",
          firma: "Remington",
          model: "D5706",
          tag: "Uroda",
          image: "https://f01.esfr.pl/foto/9/49549483769/aaa4e338610f3df0ba58832ae063375d/remington-d5706,49549483769_8.jpg",
          dostepny: true
        },
        {
          id: 1,
          name: "Blender",
          cena: 379,
          opis: "Funkcja Turbo, system próżniowy",
          firma: "Bosh",
          model: "ErgoMixx",
          tag: "Kuchnia",
          image: "https://f00.esfr.pl/foto/5/57868978513/ea7c8a3239227ae7f62237723a28d91a/bosch-blender-ms6cb61v5,57868978513_8.jpg",
          dostepny: true
        },
        {
          id: 1,
          name: "Wyciskarka wolnoobrotowa",
          cena: 128.99,
          opis: "Cicha praca, łatwe czyszczenie",
          firma: "Raven",
          model: "EWW002",
          tag: "Kuchnia",
          image: "https://f01.esfr.pl/foto/5/17302048329/2cbbcc74524309b93f61459e748b885/raven-eww002,17302048329_8.jpg",
          dostepny: false
        },
        {
          id: 1,
          name: "Odkurzacz",
          cena: 128.99,
          opis: "Najcichszy a zarazem wysoce wydajny odkurzacz tradycyjny. W zestawie 5 wymiennych końowek oraz 2 worki.",
          firma: "Electrolux",
          model: "D82-4MG",
          tag: "Sprzątanie",
          image: "https://f00.esfr.pl/foto/5/59017141121/d31660af95ce3144985b89a738a76021/electrolux-odkurzacz-pure-d82-4mg,59017141121_8.jpg",
          dostepny: true
        }
      ]
    }
  },
  methods:{
    deleteProduct(id) {
      this.products = this.products.filter(product => product.id !== id)
    },
    addProduct(newProduct) {
      this.products = [...this.products, newProduct]
    },
    filterTag(tag) {
      this.products = this.products.filter(product => product.tag == tag)
    },
    applyPrice(cenaMIN, cenaMAX) {
      this.products = this.products.filter(product => product.cena > cenaMIN & product.cena < cenaMAX)
    },
    applySorting(sorting) {
      if (sorting.includes("cena"))
      {
        this.products.sort((a, b) => a.cena - b.cena);
      }
      if (sorting.includes("name"))
      {
        this.products.sort((a,b) => (a.name > b.name) ? 1 : ((b.name > a.name) ? -1 : 0))
      }
    },
    applyAvailable() {
      this.products = this.products.filter(product => product.dostepny == true)
    }
  }
}
</script>
<style>
*{
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}

.btn {
  display: inline-block;
  border: none;
  background: rgb(6, 167, 105);
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}

</style>
