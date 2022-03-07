<script>
    export default {
        data() {
            return {
                condition: true,
                error: false,
                success: false,
                score: '',
                fail: '',
                showText: true,
                users:[
                    {id:1, name: 'Russel', age: '20'},
                    {id:2, name: 'Martin', age: '21'},
                    {id:3, name: 'Jack', age: '22'},
                    {id:4, name: 'Tim', age: '23'},
                    {id:5, name: 'Berstow', age: '24'},
                    {id:6, name: 'David', age: '25'},
                    {id:7, name: 'Andre', age: '26'},
                    {id:8, name: 'Stefin', age: '27'},
                    {id:9, name: 'Kaul', age: '28'},
                ],

            }
        }, 
    
    methods: {
       
    },
}

</script>

<template>
    <div class="container">
        <h2>{{condition ? "yes" : "no"}}</h2>
        <button class="btnStyle">check it</button>
        <br>
        <button v-on:click=" error =  !error">toggle error</button>
        <button v-on:click=" success =  !success">toggle success</button>
                <!-- if conditon is more then 10 then pass else fail -->
        
        <button @click="showText = !showText">show text</button>

        <div v-if="showText" class="">
            first text<br><br>
            <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Quibusdam dicta unde doloremque sapiente quia nulla nam doloribus non in ipsa numquam, soluta ducimus ex eaque voluptate cumque dolorum. Dolor, fuga!</p>
        </div>

        <div v-else>
            second text<br><br>
            <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Quibusdam dicta unde doloremque sapiente quia nulla nam doloribus non in ipsa numquam, soluta ducimus ex eaque voluptate cumque dolorum. Dolor, fuga!</p>
        </div>
        <div v-show="showText">
            third text<br><br>
            <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Quibusdam dicta unde doloremque sapiente quia nulla nam doloribus non in ipsa numquam, soluta ducimus ex eaque voluptate cumque dolorum. Dolor, fuga!</p>
        </div>
    </div>


    <div class="container">
        <table>
            <thead>
                <tr>
                    <th>id</th>
                    <th>name</th>
                    <th>age</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="user of users" :key="user.id">
                    <td>{{ user.id }}</td>
                    <td>{{ user.name }}</td>
                    <td>{{ user.age }}</td>
                </tr>
            </tbody>
        </table>
    </div>
</template>


<style scoped>
    .container{
        width: 100%;
        max-width: 70%;
        margin: 0 auto;
        padding-bottom: 5%;
    }
    .cusinp{
        background: #fff;
        color: #000;
        margin-top: 10px;
        width:20%;
    }
    table{
        color: #fff;
        border: 1px solid #fff;

    }
    td,th{
        /* border: 1px solid #fff; */
        width: 20%;
        border-right: 1px solid white;
        border-bottom: 1px solid white;
        font-size: 20px;
    }
</style>