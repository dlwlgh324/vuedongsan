<template>
    <div v-for="(a,i) in oneroom" :key="i">    
        <img :src="oneroom[i].image" alt="" class="room-img">    
        <h4>{{oneroom[i].title}}</h4>    
        <p>{{oneroom[i].content}}</p>    
        <p>{{oneroom[i].price}}원</p>
    <!-- @click="modalOpen = true; clickData = i" -->
    </div>
</template>

<script>
export default {
    name: 'TheCard',
    props: {
        oneroom: Array,
    }
}
</script>

<style>

</style>