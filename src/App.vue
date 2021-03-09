<template>
  <div id="app">
   
      <Navbar @search="search"></Navbar>

      <div class="container-fluid mt-5"> 
        <div class="row"> 
          <div class="col-md-9">
            <Inventory @newItem="addCart" :items="items"></Inventory>
          </div>
          <div class="col-md-3">
            <Cart @removeItem="removeItem" :carts="carts"></Cart>
          </div>  
        </div> 
      </div>

  

  </div>
</template>

<script>
import Navbar from "../src/components/Navbar"
import Inventory from "../src/components/Inventory"
import Cart from "../src/components/Cart"
import Data from './Data'
export default {
  components:{
    Navbar, Inventory, Cart
  },
  data(){
    return {
      items:[],
      carts:[],
    }
  },
  mounted(){
    this.items = Data
    console.log(Data)
  },

 methods:{
   addCart(item){
     this.carts.push(item);
   },
   removeItem(index){
     this.carts.splice(index,1);
   },
   search(keyword){
     this.items = Data.filter(item=>{
       return item.title.toLowerCase().indexOf(keyword.toLowerCase()) !== -1
     })
   }
 },
  name: 'App'
}
</script>

<style>

</style>
