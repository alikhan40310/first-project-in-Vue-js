 <script>

    export default {
        data() {
            return {
                email: '',
                password: '',
                expert: '',
                range:parseInt('5'),
                image: '',
                field: null,
                passwordError: '',
                dropDownValue: '',
                rangeError: '',
                ImageError: '',
                imageUploaded: false,
            }
        },
        methods:{
            onFileChange(e) {
                let files  = e.target.files || e.dataTransfer.files;    
                if (!files.length){
                    return;
                }
                this.createFile(files[0]);
            },
            // create image file
            createFile(file) {
                let reader = new FileReader();
            
                reader.onload = (e) => {
                    this.image = e.target.result;
                    this.imageUploaded = true;
                };
                reader.readAsDataURL(file);
            },
                removeImage: function(e) {
                    this.image = '';
                    this.ImageError = '';
                    this.imageUploaded = false;
            },
            // submit form
            handleSubmit(e){
               
                if(this.password.length < 6){
                    this.passwordError = 'password must be at least 6 characters';
                    return
                }
                else {
                    this.passwordError = '';
                }
                if(this.expert === ''){
                    this.dropDownValue = 'field must be selected';
                    return
                }
                else {
                    this.dropDownValue = '';
                }
                if(this.range < 10) {
                    this.rangeError = 'range must be greater than 10';
                    return;
                }
                else {
                    this.rangeError = '';
                }
                // file upload validation
                if(this.imageUploaded === false){
                    this.ImageError = 'image must be uploaded';
                } 
                else {
                    this.ImageError = '';
                }
            }
        }
    }
 </script>

 <template >
    <div class="container">
        <div class="">
            <form @submit.prevent="handleSubmit">
                <label for="email ">Email:</label>
                <input type="email" v-model="email" placeholder="Email" class="mt-2 form-control" required>

                <label for="password">Password:</label>
                <input type="password" v-model="password" placeholder="Password" class="mt-2 form-control" required>
                <div class="error" v-if="passwordError">
                    {{ passwordError }}
                </div>

                <select name="" v-model="expert" class="mb-3 btn btn-info mt-4 col-3 text-xl-start fs-6">
                    <option class="" value="react">React</option>
                    <option value="angular">Angular</option>
                    <option value="js">JavaScript</option>
                    <option value="vuejs">VueJS</option>
                </select>
                <div class="error" v-if="dropDownValue">
                    {{ dropDownValue }}
                </div>
                <br>
                <label for="range">Select Range:</label>
                <input id="range" v-model="range" type="range" class="mt-2 form-range accent-col">
                <div class="error" v-if="rangeError">
                    {{ rangeError }}
                </div>
                <br>
                <label for="file">Select image:</label><br>
                
                <div >
                    <input @change="onFileChange" type="file" class="mt-2 mb-3 form-control accent-col">
                </div>
                <div class="error" v-if="ImageError">
                    {{ImageError}}
                </div>
                <label for="file">Select Field:</label><br>
                <div class="d-flex gap-4 mt-3">
                    <div class="form-check">
                        <input v-model="field" value="developer" class="form-check-input" type="radio" name="fieldselect" id="developer">
                        <label class="form-check-label" for="developer">
                            developer
                        </label>
                    </div>
                    <div class="form-check">
                        <input v-model="field" value="designer" class="form-check-input" type="radio" name="fieldselect" id="designer">
                        <label class="form-check-label" for="designer">
                        designer
                        </label>
                    </div>
                </div>
                <button class="btn btn-primary mt-4">Submit</button>
            </form>
            <div class="itemsCenter">
                <div class="binding-result">
                    <p>Email: {{email}}</p>
                    <p>Password: {{password}}</p>
                    <p>Developer: {{expert}}</p>
                    <p>Range: {{range}}</p>
                    
                    <div v-if="image">
                        <img :src="image" />
                        <button class="btn btn-danger" @click="removeImage">Remove image</button>
                    </div>
                    <p>Field: {{field}}</p>
                </div>
            </div>
        </div>
    </div>
 </template>

 <style scoped>
form{
    max-width: 60%;
    margin: 30px auto;
    background: white;
    text-align: left;
    padding: 40px;
    border-radius: 10px;
    box-shadow: 0px 0px 10px rgba(0,0,0,0.5);
    color: #000;
    margin-top: 5%;
}
input{
    font-size: 1.2rem;
}
label{
    letter-spacing: 2px;
    text-transform: uppercase;
    font-weight: 700;
    color: rgb(92, 91, 91);
    font-size: 0.8rem;
}
.itemsCenter{
    display: flex;
    justify-content: center;
    flex-direction: column;
    margin-left: 16.2rem;
}
img {
  width: 20%;
  display: block;
  margin-bottom: 10px;
  background-attachment: fixed;
}
.error{
    font-size: 0.8rem;
    color: red;
}
 </style>