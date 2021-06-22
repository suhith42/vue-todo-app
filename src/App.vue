<template>

  <div id="app">
    <h1>TODO App</h1>
    <AddItem v-bind:pendingNumber="pendingList.length" v-bind:completedNumber="completedList.length" v-on:addNewItem="addNewItem($event)"/>
    <PendingItems v-bind:pendingList="pendingList" v-on:moveToCompleted="moveToCompleted($event)" />
    <CompletedItems v-bind:completedList="completedList" v-on:moveToPending="moveToPending($event)" />

  </div>
</template>

<script>
import AddItem from './components/AddItem.vue'
import CompletedItems from './components/CompletedItems.vue'
import PendingItems from './components/PendingItems.vue'

export default {
  name: 'App',
  components: {
    AddItem,
    CompletedItems,
    PendingItems,
    
  },
  data(){
    return{
      pendingList:[],
      completedList:[]
    }
  },
  methods:{
    addNewItem: function(newItem){
      this.pendingList.push(newItem)
      console.log(this.pendingList);

    },
    moveToCompleted: function(item){
      this.completedList.push(this.pendingList[item])
      this.pendingList.splice(item,1)
    },
    moveToPending: function(item){
      this.pendingList.push(this.completedList[item])
      this.completedList.splice(item,1)
    },
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  list-style-position: inside;
}
  .table{
        margin-left: auto;
        margin-right: auto;
        text-align: left;
        width: 50vw;
        table-layout: fixed;
  }

  .numCol{
    width: 5%;
  }
  .itemCol{
    width: 80%
  }
  .btnCol{
    width: 15%;
  }
  .table tr{
    height: 6vh;
  }
  .emptyListMsg{
    color: #6b6b6b;
  }
</style>
