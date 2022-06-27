<template>
    <transition name="fade">
        <TheModal :oneroom="oneroom" :clickData="clickData" :modalOpen="modalOpen" @closethemodal="modalOpen = false" />
    </transition>
    <div class="menu">
        <a href="#" v-for="a in meuns" :key="a">{{a}}</a>
    </div>
    
    <TheDiscount v-if="showDiscount == true" />
    
    <button @click="abcSort">가나다순 정렬</button>
    <button @click="fiftySort">50만원미만</button>
    <button @click="priceSort">가격순 정렬</button>
    <button @click="priceReSort">가격역순 정렬</button>
    <button @click="sortBack">되돌리기</button>
    <!-- v-bind = "object" :이름 = "object.name" :나이="object.age" -->
    <TheCard @openthemodal="modalOpen = true; clickData = $event" v-for="(a,i) in oneroom" :key="i" :oneroom="oneroom[i]" />
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
            showDiscount: true,
            oneroomOrigin: [...data],
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
        },
        abcSort() {
            this.oneroom.sort(function(a, b) {
                if (a.title < b.title) return -1;
            });
        },
        fiftySort() {
            this.oneroom = this.oneroom.filter(function(data) {
                return data.price < 500000
            });
        },
        priceSort() {
            this.oneroom.sort(function(a, b) {
                return a.price - b.price
            });
        },
        priceReSort() {
            this.oneroom.sort(function(a, b) {
                return b.price - a.price
            });
        },
        sortBack() {
            this.oneroom = [...this.oneroomOrigin];
        },
    },
    // mounted() {
    //     setTimeout(() => {
    //         this.showDiscount = false;
    //     }, 2000);
    // },
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

.fade-enter-from {
    opacity: 0;
}

.fade-enter-active {
    transition: all 1s;
}

.fade-enter-to {
    opacity: 1;
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
