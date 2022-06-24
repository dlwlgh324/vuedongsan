<template>
    <div class="black-bg" v-if="modalOpen == true">
        <div class="white-bg">
            <img :src="oneroom[clickData].image" alt="" style="width:100%">
            <h4>{{oneroom[clickData].title}}</h4>
            <p>{{oneroom[clickData].content}}</p>
            <!-- <input v-model.number="month"> -->
            <input type="range" v-model.number="month" min="1" max="12">
            <p>{{month}}개월 선택함 : {{oneroom[clickData].price * month}}원</p>
            <button @click="$emit('closethemodal')">닫기</button>
        </div>
    </div>
</template>

<script>
export default {
    name: 'TheModal',
    data() {
        return {
            month: 1,
        }
    },
    // watch: {
    //     month(a) {
    //         // ex) 사용자가 month를 글자로 입력하면 경고문 띄워줘
    //         // 사용자가 month에 입력한 데이터가 13보다 크면 경고문 띄워줘
    //         if(a >=13){
    //             alert('13이상 입력하지마세요');
    //             this.month = 1
    //         }
    //         // isNaN()안에 숫자를 입력하면 false 글자입력하면 true가 나옴
    //         if (isNaN(a) == true) {
    //             alert('문자입력하지마세요');
    //             this.month = 1
    //         }
    //     }
    // },
    props: {
        oneroom: Array,
        clickData: Number,
        modalOpen: Boolean,
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