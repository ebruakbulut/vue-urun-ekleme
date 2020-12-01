<template>
  <div v-if="productList.length>0">
    <h3 class="text-center">Eklenen Ürünlerin Listesi</h3>
    <hr>
    <div class="row product-container">
      <app-product v-for="p in productList">
        <img class="card-img-top" :src="p.selectedImage" :alt="p.title">
        <div class="card-body">
          <h5 class="card-title">{{p.title}}</h5>
          <small><strong>Adet : </strong> {{p.count}}</small>
          <br>
          <small><strong>Fiyat : </strong> {{p.price}} </small>
          <br>
          <small><strong>Tutar : </strong> {{p.totalPrice}} </small>
        </div>
      </app-product>
    </div>
  </div>
</template>
<script>
import Product from "./Product"
import {eventBus} from "../main";

export default {
  components:{
    appProduct:Product
  },
  data(){
    return{
      productList: []
    }
  },
  methods : {

  },
  created(){
    eventBus.$on("data",(product)=>{
      if(this.productList.length<11){
        this.productList.push(product);
        eventBus.$emit("progressUpdate",this.productList.length)
      }else{
        alert("Daha fazla ürün ekleyemezsiniz !!")
      }


    })
  }
}
</script>