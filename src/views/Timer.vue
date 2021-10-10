<template>
  <Clock :heading="title" :color="color"></Clock>
</template>

<script>
import Clock from '@/components/Clock.vue'
export default {
    data(){
        return{
            title: 'Digital Clock`s',
            color: 'yellow'
        }

    },
    components:{
        Clock
    }

}
</script>

<style>

</style>