<script>
    // siign up form
    export default {
        data() {
            return{
                email: '',
                password: '',
                role: 'designer',
                terms: false,
                tempSkill: '',
                skills: [],
            }
        },
        methods: {
            addSkill(e) {
                if (e.key === ',' && this.tempSkill) {
                    if (!this.skills.includes(this.tempSkill)){
                        this.skills.push(this.tempSkill);
                    }
                    
                    this.tempSkill = '';
                }
            },
            // delete skill from array
            deleteSkills(skill) {
                this.skills = this.skills.filter((item) => {
                    return skill !== item;
                });
            },
        }
    }
    // when a user clicks on a skill, delete that skillls..
</script>


<template>
    <form>  
        <label for="">Email</label>
        <input placeholder="Enter Email Address" v-model="email" type="email" required>

        <label for="">Password:</label>
        <input placeholder="Enter Password" v-model="password" type="password" required>


        <label for="">Role:</label>
        <select v-model="role">
            <option value="developer">web developer</option>
            <option value="designer">web designer</option>
            <option value="other">other</option>
        </select>

        <label for="">Skills:</label>
        <input @keyup.alt="addSkill" type="text" v-model="tempSkill">

        <div v-for="skill in skills" :key="skill" class="pill">
            <span @click="deleteSkills(skill)"> {{skill}} </span>
        </div>

        <div class="terms">
            <input type="checkbox" required v-model="terms">
            <label >Accepts terms and conditons</label>
        </div>
    </form>

    <p>Email: {{ email }}</p>
    <p>Password: {{ password }}</p>
    <p>Role: {{ role }}</p>
    <p>Terms accepted: {{ terms }}</p>





</template>

<style scoped>
   form{
       max-width: 420px;
       margin: 3px auto;
       background: white;
       text-align: left;
       padding: 40px;
       border-radius: 10px;
   }
   label{
       color: #aaa;
       display: inline-block;
       margin: 25px 0 15px;
       font-size: 0.6rem;
       text-transform: uppercase;
       letter-spacing: 1px;
       font-weight: bold ;
   }
   input,select{
       display: block;
       padding: 10px 6px;
       box-sizing: border-box;
       border: none;
       border-bottom: 1px solid #ddd;
       color: #555;
       width: 100%;
        font-size: 1rem; 
        background: transparent;   
   }
   input:focus{
         outline: none;
   }
   input[type="checkbox"]{
       width: 16px;
       height: 16px;
       border: 1px solid #ddd;
       border-radius: 4px;
       margin:0 10px 0 0;
       position: relative;
       top: 2px;
       cursor: pointer;
       display: inline-block;
   }
   .pill{
       display: inline-block;
       margin: 20px 10px 0 0;
       padding: 6px 12px;
       border-radius: 20px;
       font-size: 12px;
       letter-spacing: 1px;
        background:#eee ;
       color:#777;
   }
</style>
