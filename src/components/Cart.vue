<template>
      <div class="card" style="width: 18rem;">
                <div class="card-header">
                  Cart List
                </div>
                <ul class="list-group list-group-flush">
                    <li v-for="(item, index) in carts" :key="index" class="list-group-item">
                        <div class="float-left"><button class="btn btn-danger" @click="removeItem(index)">X</button> {{item.title}} </div>
                        <div class="float-right">
                             <strong> ${{item.price}} </strong>
                        </div>
                    </li>
                </ul>
                <div class="card-header">
                    <div class="float-left"> Total:</div>
                    <div class="float-right"> <strong> ${{totalPrice}} </strong>  </div>
                </div>
            </div>
</template>

<script>
export default {
    
    props:['carts'],
    name:'Cart',
    computed:{
        totalPrice(){
            var total = 0;
            this.carts.forEach(element =>{
                total += parseFloat(element.price);
            })
            return total;
        }
    },
    methods:{
        removeItem(index){
            this.$emit('removeItem', index);
        }
    }
}
</script>

<style>

</style>