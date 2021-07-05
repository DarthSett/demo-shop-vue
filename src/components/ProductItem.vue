<template>
    <div class='scrolling-component'>
        <div class="product-item">
            <div class="image">
                <img :src=product.image>
            </div>
            <div class="product">
                <p class="product-brand"><small> {{product.brand}} </small></p>
                <p class="product-name">{{product.name}}</p>
                <p>{{product.weight}}</p>
                <p> </p>
                <br>
                <p><s>Rs {{product.mrp}}</s></p>
                <p><strong>Rs {{product.sp}}</strong></p>
                <button><strong>Add</strong></button>
            </div>
        </div>
    </div>
</template>

<script>

    export default {
        name: "ProductItem",
        props: {
            product: {
                type: Object,
                required: true
            }
        }
    }
</script>

<style scoped>
    .product-item {
        /*margin-right: 80px;*/
        /*margin-bottom: 5px;*/
        /*width: 100%;*/
        /*padding: 20px;              !*sets the padding from borders of div .user-profile_user-panel*!*/
        background-color: #FFFFFF;
        border-radius: 5px;         /*rounded edge*/
        border: 1px solid #dfe3e8;  /*sets the width,style,and color of border*/
        box-sizing: border-box;
        transition: all 0.25s ease;
        color: black;
        display: grid;
        grid-template-columns: 1fr 2fr;

    }

    .product-name{
        text-align: left;
    }

    p{
        margin: 0;
    }

    .image{
        padding-top: 1em;
    }


    .product{
        display: flex;
        flex-direction: column;
        align-items: flex-start;
        margin-bottom: 1em;
    }

    button{
        margin-left: auto;
        background-color: teal;
        border: 0 none;
        border-radius: 5px;
        margin-right: 1em;
        color: white;
        padding: 0.5em 2em;
    }
    /*&:hover{*/
    /*    transform: scale(1.1,1.1); !*hover mechanism*!*/
    /*}*/


</style>
