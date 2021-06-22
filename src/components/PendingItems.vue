<template>
    <div class="container">
         <h2>Pending items</h2>
         <!-- <button v-on:click="completed('My custom message')">cxczxc</button> -->
         <p class="emptyListMsg" v-if="pendingList.length==0">No items to show</p>
        <table class="table">
            <tbody>
                <tr v-for="(item,index) in pendingList" :key="index">
                    <td class="numCol">{{ index + 1 }}.</td>  
                    <td class="itemCol">{{ item }}</td> 
                    <td class="btnCol"> <button v-on:click="completed(index)">✔</button></td>  
                </tr>
            </tbody>
        </table>

        <!-- <ol class="list">
            <li v-for="(item,index) in pendingList" :key="item">
                {{item}}
                <button v-on:click="completed(index)">✓</button>
            </li>
        </ol> -->
    </div>
   
</template>

<script>
export default {
    props:['pendingList'],
    data(){
        return{}
    },
    methods:{
        completed: function(index){
            this.$emit('moveToCompleted',index)
            // console.log(index);
        }
    }
}
</script>

<style scoped>

</style>