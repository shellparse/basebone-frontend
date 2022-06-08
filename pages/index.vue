<template>
<div class="px-2 h-screen bg-gradient-to-b from-green-200 to-blue-200">
  <div id="monitor" class="h-auto w-auto h-3/6 px-2">
  <Create class="m-auto" v-if="show==='create'"/>
  <List class="m-auto" v-else-if="show==='list'" />
  <Delete class="m-auto" v-else-if="show==='delete'" />
  </div>
  <div class="flex -mx-2 h-3/6">
    <div class="w-1/3 px-2 m-auto">
      <div class="h-12 flex items-center justify-center">
        <button @click="show='create'" class="bg-gradient-to-r from-green-400 to-blue-500 hover:from-indigo-500 via-purple-500 to-pink-500 text-white font-bold py-2 px-4 border-b-4 border-blue-700 hover:border-blue-500 rounded">
        Create User
    </button>
      </div>
    </div>
    <div class="w-1/3 px-2 m-auto">
      <div class="h-12 flex items-center justify-center">
        <button @click="show='list'" class="bg-gradient-to-r from-green-400 to-blue-500 hover:from-indigo-500 via-purple-500 to-pink-500 text-white font-bold py-2 px-4 border-b-4 border-blue-700 hover:border-blue-500 rounded">
        list Users
    </button>
      </div>
    </div>
    <div class="w-1/3 px-2 m-auto">
      <div class="h-12 flex items-center justify-center">
      <button @click="show='delete'" class="bg-gradient-to-r from-green-400 to-blue-500 hover:from-indigo-500 via-purple-500 to-pink-500 text-white font-bold py-2 px-4 border-b-4 border-blue-700 hover:border-blue-500 rounded">
        delete Users
    </button>
      </div>
    </div>
  </div>
 

</div>


</template>

<script>
import List from '../components/List.vue';
import Delete from '../components/Delete.vue';
import Create from '~/components/Create.vue';
export default {
    name: "IndexPage",
    components: {List, Delete, Create },
    methods:{
      showForm(form){

      }
    },
    data(){
      return{
        show:""
      }
    }
}
</script>
