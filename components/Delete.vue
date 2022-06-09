
<template>
<div class="content flex flex-col h-auto w-3/6 py-10">
      <form @submit.prevent="handleDeleteSubmit" id="delete-form" name="delete" class="py-10 flex flex-col text-center bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4">
        <label class="my-2 block text-gray-700 text-sm font-bold mb-2" for="id">
          Id:
        </label>
        <input class="text-center bg-gray-200 appearance-none border-2 border-gray-200 rounded w-full py-2 px-4 text-gray-700 leading-tight focus:outline-none focus:bg-white focus:border-blue-500" name="id" id="id" />
        <input class="mt-5 shadow bg-blue-500 hover:bg-blue-300 focus:shadow-outline focus:outline-none text-white font-bold py-2 px-4 rounded" type="submit" value="Submit" />
      </form>
    </div>
</template>

<script>
import UserCard from "./UserCard.vue";
export default {
  component:{UserCard},
  methods:{
    async handleDeleteSubmit(event){
          const form = event.currentTarget;
            try {
                const formData = new FormData(form);
                const plainFormData = Object.fromEntries(formData.entries());
                const formDataJsonString = JSON.stringify(plainFormData);
                fetch(`https://f7b0efc1-99d2-4a67-a280-f2632dc7ed81.mock.pstmn.io/users?_id=${plainFormData.id}`, {
                    method: "DELETE"
                    // headers: {
                    //     "Content-Type": "application/json",
                    //     Accept: "application/json",
                    // },
                    // body: formDataJsonString
                }).then((response) => response.json()).then((result) => {
                  result.attributes[0].uri="https://robohash.org/"+result.attributes.email
                    this.$emit("deletesubmit", result.attributes[0]);
                });
            }
            catch (e) {
                console.error(e);
            }
    }
  },
  data(){
    return{
      form:document.getElementById("delete-form")
    }
  }
} 
</script>