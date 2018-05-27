<template>
  <form id="app">
  <div class="hello">
    <br>
    <div>
      <div class="columns">
  <div class="column"><span class="button is-danger is-rounded"><p class="title is-2 is-spaced">{{msg}}</p></span></div>
</div>
  <div class="columns">
  <div class="column"><a>Name Product : <input class="input is-small" type="text" placeholder="ชื่อสินค้า" v-model="nameproduct"></a></div>
  </div>

  <div class="columns">
    <div class="column"><a>Price Product : <input class="input is-small" type="text" placeholder="ราคาสินค้า" v-model="priceproduct"></a></div>
    </div>

  <div class="columns">
    <div class="column"><a>Number Product : <input class="input is-small" type="text" placeholder="จำนวนสินค้า" v-model="numberproduct"></a></div>
      </div>

      <div class="columns">
        <div class="column"><a>picture Product : <input class="input is-small" type="text" placeholder="รูปสินค้า" v-model="pictureproduct"></a></div>
          </div>

  <a class="button is-danger is-outlined" @click="addproduct()">ตกลง</a>
  <a class="button is-info is-outlined" @click="clearproduct()">ยกเลิก</a>
  <router-link to='showproduct'><a class="button is-success is-outlined">หน้าสินค้า</a></router-link>
</div>
</div>
</form>
</template>
<script>
import firebase from 'firebase'
const config = {
  databaseURL: 'https://product-9323d.firebaseio.com'
}
let app = firebase.initializeApp(config)
let db = app.database()
let productRef = db.ref('product')
export default {
  name: 'HelloWorld',
  firebase: {
    product: productRef
  },
  data () {
    return {
      msg: 'Product Store',
      nameproduct: '',
      priceproduct: '',
      numberproduct: '',
      pictureproduct: ''
    }
  },
  methods: {
    addproduct () {
      let tmp = {
        nameproduct: this.nameproduct,
        priceproduct: this.priceproduct,
        numberproduct: this.numberproduct,
        pictureproduct: this.pictureproduct
      }
      productRef.push(tmp)
      this.nameproduct = ''
      this.priceproduct = ''
      this.numberproduct = ''
      this.pictureproduct = ''
    },
    clearproduct () {
      this.nameproduct = ''
      this.priceproduct = ''
      this.numberproduct = ''
      this.pictureproduct = ''
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
input {
    width: 30%;
}
</style>
