<template>
    <div class>
        <div v-bind:key="product.id" v-for="product in products">
            <div class="container">
                <ProductItem v-bind:product="product" v-on:del-product="$emit('del-product', product.id)" v-on:filter-tag="$emit('filter-tag', product.tag)" v-on:open-edit="$emit('open-edit', product.id)"/>
            </div>
        </div>
    </div>
</template>
<script>
import ProductItem from './ProductItem.vue';

export default {
    name: "Products",
    components: {
        ProductItem
    },
    props: ["products"]
}
</script>
<style scoped>
    .container {
        background: #f4f4f4;
        align-items: center;
        grid-template-columns: 100px 50px 100px;
        grid-template-rows: 120px auto 120px; 
        column-gap: 10px;
        row-gap: 15px;
    }
</style>
