<template>
    <div class="black-bg" v-if="modalOpen == true">
        <div class="white-bg">    
            <img :src="oneroom[clickData].image" alt="" style="width:100%">    
            <h4>{{oneroom[clickData].title}}</h4>   
            <p>{{oneroom[clickData].content}}</p>
            <p>{{oneroom[clickData].price}}원</p>
            <!-- <button @click="modalOpen = false">닫기</button> -->
        </div>    
    </div>
</template>

<script>
export default {
    name: 'TheModal',
    props : {
        oneroom : Array,
        clickData : Number,
        modalOpen : Boolean,
    }
}
</script>

<style>

.black-bg {
    position: fixed;
    padding: 20px;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.5);
}

.white-bg {
    width: 50%;
    background-color: #fff;
    border-radius: 8px;
    padding: 20px;
    margin: 0 auto;
}
</style>