<template>
    <div class="nav justify-content-end">
        <button class="btn btn-primary cartbtn" type="button" data-bs-toggle="offcanvas" data-bs-target="#offcanvasRight" aria-controls="offcanvasRight">
          <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-bag" viewBox="0 0 16 16">
          <path d="M8 1a2.5 2.5 0 0 1 2.5 2.5V4h-5v-.5A2.5 2.5 0 0 1 8 1zm3.5 3v-.5a3.5 3.5 0 1 0-7 0V4H1v10a2 2 0 0 0 2 2h10a2 2 0 0 0 2-2V4h-3.5zM2 5h12v9a1 1 0 0 1-1 1H3a1 1 0 0 1-1-1V5z"/>
          </svg>
          <span class="badge text-bg-secondary totalqty">{{ totalQty }}</span>
        </button>
    </div>
</template>

<script>
import { mapGetters } from "vuex";
export default {
  name: "Header",
  computed: {
    ...mapGetters(["cart"]),
    totalQty() {
      return this.cart.reduce((a, b) => a + b.qty, 0);
    },
  },
}
</script>

<style lang="scss" scoped>
.totalqty{
    background: #fff;
    color: #000;
    border-radius: 12px;

}
.cartbtn{
    position: fixed;
    top: 0;
    right: 0;
    color: lightseagreen;
    background: #00a8a275;
    padding: 16px;
    font-size: 15px;
    border-radius: 0%;
    border: none
}
.cartbtn:hover, .cartbtn:focus{
  color: lightseagreen;
  background: #00a8a275;
  outline: none;
  box-shadow: none;
  border: none;
}
</style>