<script>
    export default {
        data() {
            return {
                count: 0
            }
        }, 
    
    methods: {
        increment() {
            this.count++;
            console.log('count:', this.count);
        },
        decrement() {
            this.count--
        },
        reset() {
            this.count = 0
        }
    },
    // mounted(){
    //     console.log(`the initial count is:   ${this.count}`)
    // }
}
</script>

<template>
    <h1>count is {{count}}</h1>
    <div class="itemsCenter">
        <button class="btn" @click="increment">add</button>
        <button class="btn" @click="decrement">decrement value</button>
        <button class="btn" @click="reset">reset</button>
    </div>
</template>

<style scoped>
h1{
    margin-top: 10rem;
    text-align: center;
}
 .itemsCenter{
     display: flex;
     justify-content: center;
     gap:10px;
     margin-top: 10px;
 }
 .btn{
    background-color: rgb(0, 119, 255);
    color: white;
    padding: 10px 20px;
    border: 1px solid transparent;
    border-radius: 4px;
    font-size: 18px;
    cursor: pointer;
    text-transform: capitalize;
    }
</style>
