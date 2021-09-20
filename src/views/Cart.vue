<template>
  <div class="cart">
    <h1>Carts</h1>
    <div class="product-wrapper">
        <table>
          <tbody>
            <!-- <tr class="row">
              <td>
                <img src="https://via.placeholder.com/50">
              </td>
              <td>
                <p>Product title</p>
              </td>
              <td>
                <h5>Rp.100.000</h5>
              </td>
              <td>
                  <div>hapus</div>
              </td>
            </tr>
            <tr class="row">
              <td>
                <img src="https://via.placeholder.com/50">
              </td>
              <td>
                <p>Product title</p>
              </td>
              <td>
                <h5>Rp.100.000</h5>
              </td>
              <td>
                  <div>hapus</div>
              </td>
            </tr>
            <tr class="row">
              <td>
                <img src="https://via.placeholder.com/50">
              </td>
              <td>
                <p>Product title</p>
              </td>
              <td>
                <h5>Rp.100.000</h5>
              </td>
              <td>
                  <div>hapus</div>
              </td>
            </tr> -->
            <tr class="row" v-for="(item, idx) in carts" :key="idx">
              <td>
                <img :src="item.image">
              </td>
              <td>
                <p>{{ item.title }}</p>
              </td>
              <td>
                <h5>{{ item.price }}</h5>
              </td>
              <td>
                <button @click="removeItem(item.id)">hapus</button>
              </td>
            </tr>
          </tbody>
          <tfoot>
            <tr >
              <td colspan="4">
                <button @click="checkout()">Checkout</button>
              </td>
            </tr>
          </tfoot>
        </table>

    </div>
  </div>
</template>

<style scoped lang="scss">
$orange: #f37021;
$white: #fff;

// layout
.product-wrapper {
  margin: 0 auto;
  padding: 1em;
  width: 75%;

  table {
    margin: 0 auto;
    width: 70%;

    .row {
      border-bottom: #ccc 1px;
    }

    button {
      padding: 1em;
      background: $orange;
      color: $white;
      border: none;
      font-size: 1em;
      font-weight: bold;
      width: 100px;
      cursor: pointer;
      float: right;
    }
  }

  
}
</style>

<script>
import { mapActions, mapGetters} from 'vuex'

export default {
  name: 'Cart',
  computed: {
    ...mapGetters(['carts']),
  },
  created() {
    this.getCarts()
  },
  methods: {
    ...mapActions(['getCarts', 'deleteCartItem']),
    checkout() {
      return this.$router.push('/checkout')
    },
    removeItem (productId) {
      this.deleteCartItem(productId)
    }
  }
}
</script>