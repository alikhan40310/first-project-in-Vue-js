import './SignUpForm.css';

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


