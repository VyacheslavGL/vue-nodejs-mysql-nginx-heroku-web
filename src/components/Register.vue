<template>
    <div>
        <h2 id="mess"></h2>
        <h4>Register</h4>
        <form>
            <label for="name">Name</label>
            <div>
                <input id="name" type="text" v-model="name" required autofocus>
            </div>

            <label for="email" >E-Mail Address</label>
            <div>
                <input id="email" type="email" v-model="email" required>
            </div>

            <label for="password">Password</label>
            <div>
                <input id="password" type="password" v-model="password" required>
            </div>

            <label for="password-confirm">Confirm Password</label>
            <div>
                <input id="password-confirm" type="password" v-model="password_confirmation" required>
            </div>

            <label for="password-confirm">Is this an administrator account?</label>
            <div>
                <select v-model="is_admin">
                    <option value=1>Yes</option>
                    <option value=0>No</option>
                </select>
            </div>

            <div>
                <button type="submit" @click="handleSubmit">
                    Register
                </button>
            </div>
        </form>
<!--        <h1>Is admin != null: {{is_admin != null}}</h1>-->
<!--        <h1>Is admin: {{is_admin}}</h1>-->
    </div>
</template>

<script>
    export default {
        props : ["nextUrl"],
        data(){
            return {
                name : "",
                email : "",
                password : "",
                password_confirmation : "",
                is_admin : null
            }
        },
        methods : {
            handleSubmit(e) {
                e.preventDefault();

                if (this.password === this.password_confirmation && this.password.length > 0)
                {
                    // let url = "http://localhost:3000/register";
                    // let url = "http://localhost:5000/register";
                    let url = "https://vue-node-mysql-heroku-web.herokuapp.com/register";
                    // if(this.is_admin != null && this.is_admin === 1) url = "http://localhost:3000/register-admin";
                    // if(this.is_admin != null && this.is_admin === 1) url = "http://localhost:5000/register-admin";
                    if(this.is_admin != null && this.is_admin === 1) url = "https://vue-node-mysql-heroku-web.herokuapp.com/register-admin";
                    this.$http.post(url, {
                        name: this.name,
                        email: this.email,
                        password: this.password,
                        is_admin: this.is_admin
                    })
                        .then(response => {
                            console.log('register response - ', response);
                            localStorage.setItem('user',JSON.stringify(response.data.user));
                            localStorage.setItem('jwt',response.data.token);

                            if (localStorage.getItem('jwt') != null){
                                this.$emit('loggedIn');
                                if(this.$route.params.nextUrl != null){
                                    this.$router.push(this.$route.params.nextUrl)
                                }
                                else{
                                    this.$router.push('/')
                                }
                            }
                        })
                        .catch(error => {
                            /*if (error.response && error.response.status === 404){
                                return document.getElementById('mess').innerText = error.response.data;
                            }*/
                            console.error('This error in Registration - ', error);
                        });
                } else {
                    this.password = "";
                    this.passwordConfirm = "";

                    return alert("Пароли не совпадают")
                }
            }
        }
    }
</script>

<style scoped>

</style>