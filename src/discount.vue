<template>
    <div class="discount">
        <h4>지금 결제하면 {{percent}}% 할인</h4>
    </div>
</template>

<script>
export default {
    name: 'TheDiscount',
    data() {
        return {
            percent: 30,
        }
    },
    mounted(){
    var timer = setInterval(()=>{
    this.percent--;
    // 0 이하면 멈춤
    if(this.percent==0){
        clearInterval(timer);
    }
    }, 1000);
    },
}
</script>

<style>
.discount {
    background-color: #eee;
    padding: 10px;
    margin: 10px;
    border-radius: 10px;
}
</style>