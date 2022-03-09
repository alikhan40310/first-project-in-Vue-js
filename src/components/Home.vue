<script>
    import Child from './Child.vue';

    export default {
        name: 'Home',
        components: {
            Child,
        },
        data() {
            return {
                name: 'ali',
                user: {
                    name: 'ali',
                    email: 'alikhan40310@gmail.com'
                }
            }
        },
        methods: {
            getData(){
                if(this.user.name === this.name){
                    this.name = this.user.email;
                }
                else {
                    this.name = this.user.name;
                }
            }
        }
    }
</script>

<template>
    <div class="container">
        <h2>Passed data to child components</h2>
        <h3>the following data are from child  </h3>
        <Child :name="name" :getData="getData"></Child>
    </div>
</template>
