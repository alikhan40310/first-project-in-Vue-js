<script>
    export default {
        name: 'Child',
        props: {
            name: String,
            data: Object,
            getData: Function, 
        }
    }
</script>

<template>
    <div class="container">
        <h2>{{name}}</h2>
        <button @click="getData()" class="btn btn-primary">Click here</button>
        
    </div>
</template>