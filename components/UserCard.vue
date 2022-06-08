<template>
<section class="w-64 mx-auto bg-[#20354b] rounded-2xl px-8 py-6 shadow-lg">
      <div v-if="user.email" class="text-center p-2 mb-2 text-sm text-green-700 bg-green-100 rounded-lg dark:bg-green-200 dark:text-green-800" role="alert">
  <span class="text-center font-medium">user created!</span>
</div>
        <div class="mt-6 w-fit mx-auto">
            <img :src=user.uri class="rounded-full w-auto h-3/6 " alt="profile picture" srcset="">
        </div>

        <div class="text-fuchsia-900 mt-8 ">
            <h2 class="font-bold text-2xl tracking-wide">{{user.email}}</h2>
        </div>
        <p class="text-emerald-400 font-semibold mt-2.5" >
            {{user.msisdn}}
        </p>

        <div class="mt-3 text-white text-sm text-green-700">
            Type: {{user.user_type}}<br>
            Free Items: {{user.free_premium_items}}
        </div>

    </section>
</template>

<script>
export default {
  props: {
      user:Object
  },
  created() {
    // props are exposed on `this`
    console.log(this.user)
  }
}
</script>