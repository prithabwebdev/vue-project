<template>
  <div class="offcanvas offcanvas-end" tabindex="-1" id="offcanvasRight" aria-labelledby="offcanvasRightLabel">
    <div class="offcanvas-header">
      <h5 class="offcanvas-title" id="offcanvasRightLabel">YOUR BAG ({{ cart.length }} ITEM)</h5>
      <button type="button" class="btn-close" data-bs-dismiss="offcanvas" aria-label="Close"></button>
    </div>
    <div class="offcanvas-body">
        <div v-if="!cart.length" class="alert alert-secondary" role="alert">No Product in cart!</div>
        <div  style="overflow-y: scroll; height:400px;">

          <ul class="list-group">
              <li class="list-group-item" v-for="item in cart" :key="item.id">
                  <div class="d-flex mb-3">
                      <div class="p2 item-photo">
                          <img :src="item.images[0].src" alt="title" />
                      </div>
                      <div class="p-2">
                          <h6>{{ item.title }}</h6>
                          <p>Color: Grey</p>
                          <div class="btn-group" role="group" aria-label="Basic outlined example">
                              <button type="button" @click="reduceQty(item.id)" class="btn btn-outline-primary">-</button>
                              <button type="button" class="btn btn-outline-primary">{{item.qty}}</button>
                              <button type="button" @click="addQty(item.id)" class="btn btn-outline-primary">+</button>
                          </div>
                      </div>
                      <div class="ms-auto p2">
                          <button type="button" @click="removeItemFromCart(item.id)" class="btn-close" aria-label="Close"></button>
                          <br/><br/><br/>
                          <h6 class="item-price">${{item.variants[0].price}}</h6>
                      </div>
                  </div>
              </li>
          </ul>
        </div>
    </div>
    <div class="offcanvas-footer">
      <div class="checkout p-4">
        <div class="row">
            <div class="col-6">
                <h4>SUBTOTAL</h4>
            </div>
            <div class="col-6">
                <h4>$ {{ totalPrice.toLocaleString() }}</h4>
            </div>
            <div class="col-12">
                <button class="btn bth-primary checkoutbtn">CHECKOUT</button>
                <p>Lorem ipsum is dummy text. Lorem ipsum is dummy text. Lorem ipsum is dummy text.</p>
            </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { mapGetters, mapActions } from "vuex";
export default {
  name: "Cart",
  computed: {
    ...mapGetters(["cart"]),
    totalPrice() {
      return this.cart.reduce((a, b) => a + b.qty * b.variants[0].price, 0);
    }
  },
  methods: {
    ...mapActions(["removeItemFromCart", "addQty", "reduceQty"]),
  }
};
</script>
<style scoped>
.btn-group button{
  background: #f2f2f2;
  border-color: #f2f2f2;
  color: #000;
  padding: 4px 11px;

}

.btn-group button:hover, .btn-group button:focus{
    background: #000;
    color: #fff;
    outline: none;
    box-shadow: none;
    border: none;
}

.btn-group button:nth-child(1){
border-top-left-radius:16px;
border-bottom-left-radius:16px;
}
.btn-group button:nth-child(3){
border-top-right-radius:16px;
border-bottom-right-radius:16px;
}
.offcanvas-footer{
  border-top: 1px solid #000;
}
.offcanvas-header{
  border-bottom: 1px solid #000;
}
.offcanvas-body{
  height: auto;
}
.list-group-item{
  border: none;
  border-bottom: 1px solid rgba(0, 0, 0, 0.125);
  padding: 2px;

}
.checkout{
  background: #eff5f7;
}
.checkoutbtn{
    width: 100%;
    background: #000;
    color: #fff;
    border-radius: 0%;
    border: 1px solid #000;
    font-weight: 600;
    font-size: small;
}
.item-photo{
    width: 100px;
}
.item-photo img{
    width: 100%;
}
.item-price{
    padding: 10px;
}
.btn-close{
    float: right;
}

</style>