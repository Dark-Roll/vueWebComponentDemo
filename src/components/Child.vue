<template>
    <div class="child product">
        <!-- {{"child"}} -->

        {{`Child value from parent: ${myMessage}`}}
        <br/>
        Input which can update Parent value :   <input @input="updateParentValue" >
        <br/>
        <li v-for="(product, index) in products" :key="index" >
            <!-- <input type='number' v-model="product.quantity"/> -->
            {{product.name}} 
            {{ '：　' }}
            {{product.quantity}}
            <!-- <span v-if="product.quantity==0"> sold out </span> -->
            <!-- <button @click="product.quantity -=1"> -1</button> -->
        </li>

    </div>
</template>

<script>
import Vuex from 'vuex';
import Vue from 'Vue';
Vue.use(Vuex)
export default {
    name:'child',
    props:['myMessage'],
    data(){
        return{
            products:[{
                name: 'robot',
                quantity:'2'
            },{
                name: 'eyesmedia',
                quantity:'6'
            }]
        }        
    },
    methods:{
        updateParentValue(e){
            this.$emit('child',e.target.value)
        }
    }

}

const store = new Vuex.Store({
  state: {
    count: 0
  },
  mutations: {
    increment (state) {
      state.count++
    }
  }
})
store.commit('increment')

console.log(store.state.count) // -> 1

</script>
<style lang="css" scoped>
.child{
    text-align: left;
    margin-left: 20%;
}
</style>

