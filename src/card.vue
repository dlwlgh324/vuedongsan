<template>
    <div>    
        <img :src="oneroom.image" alt="" class="room-img">    
        <h4 @click="send">{{oneroom.title}}</h4>    
        <p>{{oneroom.content}}</p>    
        <p>{{oneroom.price}}원</p>
        <!-- @click="modalOpen = true; clickData = i" -->    
        <!-- 컴포넌트 반복문 사용시 하나씩만 들고오쟝 -->    
    </div>
</template>

<script>
export default {
    name: 'TheCard',
    props: {
        oneroom: Object,
    },
    methods: {
        send() {
            this.$emit('openthemodal', this.oneroom.id);
        }
    },
}
</script>

<style>

</style>