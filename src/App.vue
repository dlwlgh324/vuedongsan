<template>
    <TheModal :oneroom="oneroom" :clickData="clickData" :modalOpen="modalOpen" @closethemodal= "modalOpen = false"/>
    
    
    <div class="menu">
        <a href="#" v-for="a in meuns" :key="a">{{a}}</a>
    </div>
    
    <TheDiscount />
    <!-- v-bind = "object" :이름 = "object.name" :나이="object.age" -->
    
    <TheCard @openthemodal="modalOpen = true; clickData = $event" v-for="(a,i) in oneroom" :key="i" :oneroom="oneroom[i]"/>
    <!-- clickData = i 라고 해도 됨 -->
</template>

<script>
import data from './assets/oneroom.js';
import TheDiscount from './discount.vue';
import TheModal from './modal.vue';
import TheCard from './card.vue';

export default {
    name: 'App',
    data() {
        return {
            object: { name: 'kim', age: 20 },
            clickData: 0,
            oneroom: data,
            modalOpen: false, //0, 1로 표현해도 됨 // 리액트는 state임
            meuns: ['Home', 'Shop', 'About'],
            card: TheCard,
        }
    },
    methods: {
        increase() {
            this.police += 1
        }
    },
    components: {
        TheDiscount,
        TheModal,
        TheCard,
    }
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
    text-decoration: none;
}

.room-img {
    width: 100%;
    margin-top: 40px;
}
</style>
