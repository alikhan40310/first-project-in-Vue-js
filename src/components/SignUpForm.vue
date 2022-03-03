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
                passwordError: '',
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
            // submit form
            handleSubmit(e) {
                // validate password
                if (this.password.length < 6) {
                    this.passwordError = 'Password must be at least 6 characters';
                    return;
                }
                else{
                    this.passwordError = '';
                }

                // validate email
                if (!this.email.includes('@')) {
                    this.passwordError = 'Email must be valid';
                    return;
                }
                // validate terms
                if (!this.terms) {
                    this.passwordError = 'You must accept terms and conditions';
                    return;
                }

            },
            // reset form
            handleReset() {
                this.email = '';
                this.password = '';
                this.role = 'designer';
                this.terms = false;
                this.skills = [];
                this.tempSkill = '';
                this.passwordError = '';
            }

        }
    }
    // now submit the form
</script>


<template>
    <form @submit.prevent="handleSubmit">  
        <label for="">Email</label>
        <input placeholder="Enter Email Address" v-model="email" type="email" required>

        <label for="">Password:</label>
        <input placeholder="Enter Password" v-model="password" type="password" required>
        <div class="error" v-if="passwordError">
            {{ passwordError }}
        </div>


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
            <input id="conditions" type="checkbox" required v-model="terms">
            <label for="conditions">Accepts terms and conditons</label>
        </div>
        <div class="btn-container">
            <!-- submit form -->
            <div class="submit">    
            <button class="btnStyle">Create an account</button>
        </div>
        <!-- reset button -->
                <div >
                <button class="btnStyle" @click="handleReset">Reset</button>
            </div>
        </div>
    </form>
    
    <div class="ItemsCenter">
        <div>
            <p>Email: {{ email }}</p>
            <p>Password: {{ password }}</p>
            <p>Role: {{ role }}</p>
            <p>Terms accepted: {{ terms }}</p>
        </div>
    </div>





</template>

<style scoped>
   form{
       max-width: 30%;
       margin: 30px auto;
       background: white;
       text-align: left;
       padding: 40px;
       border-radius: 10px;
       box-shadow: 0px 0px 10px rgba(0,0,0,0.5);
   }
   .ItemsCenter{
         display: flex;
         justify-content: left;
         align-items: center;
         text-align: left;
         flex-direction: column;
         margin-bottom: 3%;
   }
   label{
       color: rgb(128, 127, 127);
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
   .btn-container{
       display: flex;
       justify-content: center;
       gap: 10px;
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
   .submit{
       text-align: center;
   }
   .btnStyle{
       background: #0b6dff;
       border:0;
       padding: 10px 20px;
       color: white;
         border-radius: 20px;
         cursor: pointer;
         font-size: 16px;
   }
   .error{
       color:#ff0062;
       margin-top: 10px;
       font-size: 0.6rem;

   }
</style>
