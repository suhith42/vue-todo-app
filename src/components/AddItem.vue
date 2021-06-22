<template>
    <div>
        <input class="inputBox" placeholder="Add a task" type="text" v-model="newItem">
        <button v-on:click="addItem">ADD</button>
        <div class="stats">
            <p>Pending items: {{pendingNumber}}</p>
            <p>Completed items: {{completedNumber}}</p>
        </div>

    </div>

</template>

<script>
export default {
    data() {
       return{
           newItem:''
       }
    },
    props:['completedNumber','pendingNumber'],
    methods:{
        addItem: function(){
            this.$emit('addNewItem',this.newItem)
            this.newItem = ''
            // alert(this.newItem)
        }
    }
}
</script>

<style scoped>
    .stats{
        display: flex;
        justify-content: space-evenly;

    }

    .inputBox{
        height: 5vh;
        width:  30vw
    }

    button{
        height: 5vh;
        width: 10vw;
        margin-left: 2%;
    }
</style>