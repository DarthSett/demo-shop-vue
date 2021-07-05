<template>
    <div id="app" >
        <div class="navigation__logo">
            <h3>
                ShopC
            </h3>
        </div>
        <SearchBar/>
    </div>
    <div class="products-wrapper"  ref='scrollComponent'>
        <ProductItem v-for="product in state.products" :key="product.index" :product="product"/> <!-- without :key = error  Elements in iteration expect to have 'v-bind:key' directives -->
    </div>
</template>

<script>
    import SearchBar from "./components/SearchBar";
    import ProductItem from "./components/ProductItem";
    import {reactive,ref,onMounted,onUnmounted,onBeforeMount} from 'vue';
    export default {
        name: 'App',
        components: {SearchBar,ProductItem},
        setup () {
            const state = reactive({
                products:[],
                cursor: -20
            })

            function addProduct(product) {
                state.products.push({
                    index: state.products.length + 1,
                    id: product['_id'],
                    brand: product.brand,
                    name: product.name,
                    weight: product.weight,
                    mrp: product.mrp,
                    sp: product['selling price'],
                    image: product['main image']
                });
            }


            async function getProducts() {
                state.cursor += 20
                const res = await fetch('https://dukaan.bubbleapps.io/version-test/api/1.1/obj/product?limit=20&cursor='+state.cursor);
                const data = await res.json();
                const myArr = data.response.results;
                myArr.forEach(v => addProduct(v));
                console.log(state.products)
            }

            onBeforeMount(()=> {
                getProducts();
            })

            onMounted(() => {
                window.addEventListener("scroll", handleScroll)
            })

            onUnmounted(() => {
                window.removeEventListener("scroll", handleScroll)
            })
            const handleScroll = async () => {
                let element = scrollComponent.value;
                if ( element.getBoundingClientRect().bottom < window.innerHeight ) {
                    await getProducts()
                }
            }

            const scrollComponent = ref(null)
            return {
                scrollComponent,
                state,
                addProduct,
                getProducts
            }
        }
    };
</script>

<style>
#app {
  /*background-color: teal;*/
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: white;
    margin: 0;
    display: grid;
    grid-gap: 10px;
}

html {
    background-color: teal;
}

h3 {
    margin: 0; /*removes margin around h1*/
}
</style>
