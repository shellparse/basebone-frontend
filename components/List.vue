
<template>

    
<div class="mx-auto w-3/6 text-center flex overflow-x-auto rounded-2xl shadow-lg">
    <UserCard v-for="(value,index) in userlist" :user="value" :key="value.email" :isNew="false" />
</div>


</template>
<script>
import HorizontalScroll from 'vue-horizontal-scroll'
import 'vue-horizontal-scroll/dist/vue-horizontal-scroll.css'
import UserCard from '~/components/UserCard.vue';
export default {
    components: {UserCard, HorizontalScroll},
    props: {
      userlist:[]
  },
  created() {
    // props are exposed on `this`
    // console.log(this.userlist)
  }
}
</script>
