<template>
<div class="px-2 h-screen bg-gradient-to-b from-green-200 to-blue-200">
  <div id="monitor" class="h-auto w-auto h-3/4 px-2">
  <UserCard :user=user v-if="newvariable==='0'&&show!='create'&&show!='list'&&show!='delete'" :isNew="true" />
  <Create class="m-auto" v-if="show==='create'"  @submitted="updateIndex" />
  <List class="m-auto" v-else-if="show==='list'" :userlist="userlist" />
  <UserCard :user="user" v-if="deletevariable==='0'&&show!='create'&&show!='list'&&show!='delete'" :isNew="false" :isDeleted="true" />
  <Delete class="m-auto" v-else-if="show==='delete'" @deletesubmit="deleteUser" />
  </div>
  <div class="flex -mx-2 h-auto">
    <div class="w-1/3 px-2 m-auto">
      <div class="h-12 flex items-center justify-center">
        <button @click="show='create'" class="bg-gradient-to-r from-green-400 to-blue-500 hover:from-indigo-500 via-purple-500 to-pink-500 text-white font-bold py-2 px-4 border-b-4 border-blue-700 hover:border-blue-500 rounded">
        Create User
    </button>
      </div>
    </div>
    <div class="w-1/3 px-2 m-auto">
      <div class="h-12 flex items-center justify-center">
        <button @click="showList" class="bg-gradient-to-r from-green-400 to-blue-500 hover:from-indigo-500 via-purple-500 to-pink-500 text-white font-bold py-2 px-4 border-b-4 border-blue-700 hover:border-blue-500 rounded">
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
import UserCard from '~/components/UserCard.vue';
export default {
    name: "IndexPage",
    components: { List, Delete, Create, UserCard },
    methods:{
      updateIndex(variable){
        this.user=variable
        this.show="";
        this.newvariable="0"
        this.deletevariable="1"
      },
      async showList(){
         fetch("https://f7b0efc1-99d2-4a67-a280-f2632dc7ed81.mock.pstmn.io/users")
        .then(response=>response.json())
        .then((user)=>{
        this.show="list";
        this.userlist=user.attributes.map((obj)=>{
          obj.uri="https://robohash.org/"+obj.email
          return obj;
        })
        })

      },
      async deleteUser(variable){
        this.user=variable
        this.show=""
        this.deletevariable="0"
        this.newvariable="1"
      }
    },
    data(){
      return{
        show:"",
        newvariable:"1",
        user:{},
        userlist:[],
        deletevariable:"1"
      }
    }
}
</script>
