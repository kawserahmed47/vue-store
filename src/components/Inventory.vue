<template>
       <div class="row">
              <div v-for="(item, index) in items" :key="index" class="col-md-4 mt-2">
                      <div class="card" style="width: 18rem;">
                         <img :src='item.image' class="card-img-top" alt="IMG">
                         <hr>
                        <div class="card-body">
                            <div class="float-left"><p class="card-text">{{item.title}}</p></div>
                             <div class="float-right"><strong>${{item.price}}</strong></div>
                          
                        </div>
                        <div class="card-footer">
                            <button @click="addCart(item)" class="btn btn-outline-primary">Add to Cart</button>
                        </div>
                      </div>
              </div>
                
            </div>
</template>

<script>
export default {
    props:['items'],
    name:"Inventory",
    methods:{
        addCart(item){
            this.$emit('newItem', item);
        }
    }
}
</script>

<style>

</style>