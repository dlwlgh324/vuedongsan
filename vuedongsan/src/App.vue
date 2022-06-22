<template>
    <div class="black-bg" v-if="modalOpen == true">
        <div class="white-bg">
            <h4>모달팝업 타이틀</h4>
            <p>모달팝업 내용입니다.</p>
            <button @click="modalOpen = false">팝업닫기</button>
        </div>
    
    </div>
    
    <div class="menu">
        <a href="#" v-for="a in meuns" :key="a">{{a}}</a>
    </div>
    <div v-for="(a,i) in 원룸들" :key="i">
        <img :src="원룸들[i].image" alt="" class="room-img">
        <h4 @click="modalOpen = true">{{원룸들[i].title}}</h4>
        <p>{{원룸들[i].price}}원</p>
        <p>{{원룸들[i].content}}</p>
    </div>
</template>

<script>
import data from './assets/oneroom.js';
data;

export default {
    name: 'App',
    data() {
        return {
            원룸들: data,
            modalOpen: false, //0, 1로 표현해도 됨 // 리액트는 state임
            신고수: [0, 0, 0],
            meuns: ['Home', 'Shop', 'About'],
            products: ['역삼동원룸', '천호동원룸', '마포구원룸']
        }
    },
    methods: {
        increas() {
            this.신고수 += 1
        }
    },
    components: {}
}
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
}

.menu {
    background-color: darkslateblue;
    padding: 15px;
    border-radius: 5px;
}

.menu a {
    color: #fff;
    padding: 10px;
}

.room-img {
    width: 100%;
    margin-top: 40px;
}

.black-bg {
    position: fixed;
    padding: 20px;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.5);
}

.white-bg {
    width: 100%;
    background-color: #fff;
    border-radius: 8px;
    padding: 20px;
}
</style>
