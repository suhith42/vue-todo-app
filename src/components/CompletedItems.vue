<template>

    <div>
        <h2>Completed items</h2>   
        <p class="emptyListMsg" v-if="completedList.length==0">No items to show</p>
        <table class="table">
            <tbody>
                <tr class="row" v-for="(item,index) in completedList" :key="index">
                    <td class="numCol">{{ index + 1 }}.</td>  
                    <td class="itemCol">{{ item }}</td> 
                    <td class="btnCol"> <button v-on:click="pending(index)">✘</button></td>  
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
export default {
    props:['completedList'],
    
    data(){
        return{
            
        }
        
    },
    methods:{
        pending:  function(index){
            this.$emit('moveToPending',index)
        }
    }
}
</script>

<style>

</style>