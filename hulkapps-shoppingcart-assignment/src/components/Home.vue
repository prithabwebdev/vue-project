<template>
    <div class="row">
        <div class="col-3 mb-4" v-for="item in products" :key="item.id">
            <div class="card" style="width: 18rem;"> 
                
                <Carousel :wrap-around="true">
                    <Slide v-for="slide in item.images" :key="slide">
                    <div class="carousel__item">
                        <img :src="slide.src" class="card-img-top"/>
                    </div>
                    </Slide>

                    <template #addons>
                    <Pagination />
                    </template>
                </Carousel>

                <!-- <img v-for="image in item.images" :key="image" :src="image.src" class="card-img-top" /> -->
                <div class="card-body">
                    <div class="row">
                        <div class="col-6">
                            <h6 class="card-title">{{ item.title }}</h6>
                        </div>
                        <div class="col-6">
                            <h5 class="card-price">$ {{ item.variants[0].price }}</h5>
                        </div>
                    </div>
                    <a href="#" @click="addItemToCart(item)" class="btn btn-primary addtocart">ADD TO CART</a>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import { mapActions, mapGetters } from "vuex";
import { Carousel, Pagination, Slide } from 'vue3-carousel';

import 'vue3-carousel/dist/carousel.css';

export default {
  name: "Home",
  components: {
    Carousel,
    Slide,
    Pagination,
  },
  mounted() {
    this.getProducts();
  },
  computed: {
    ...mapGetters(["products"]),
  },
  methods: {
    ...mapActions(["addItemToCart", "getProducts"]),
  },
};
</script>

<style scoped>
.carousel__pagination{
    margin-bottom: 0%;
}
.addtocart{
    width: 100%;
    background: #fff;
    color: #000;
    border-radius: 0%;
    border: 1px solid #000;
    font-weight: 600;
    font-size: small;
}
.addtocart:hover, .addtocart:focus{
    background: #000;
    color: #fff;
    outline: none;
    box-shadow: none;
    border: none;
}
.card{
    border: none;
}
.card-body{
    padding: 3% 0%;
}

</style>