<template>
<div><h1>Login Page</h1>
        <div class="box">
            <div class="container">
                <label for="uname">
                    <b>Username</b>
                </label>
                <input v-model="email" type="email" placeholder="Enter your email id" name="uname" required />
                <p class="errMsg" v-if="emailErrMsg">Enter a valid email</p>
                <label for="psw">
                    <b>Password</b>
                </label>
                <input v-model="password" type="password" placeholder="Enter Password" name="psw" required/>
                <p class="errMsg" v-if="passwordErrMsg">Password length should be more than 8 characters</p>

                <button @click="loginFun">Login</button>
            </div>
        </div>
        </div>

</template>  

<script>
export default {
    data() {
        return {
            email: "",
            password: "",
            emailErrMsg: true,
            passwordErrMsg: true,
        }
    },
    watch: {

        email(value) {
               const re = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
            if (re.test(value)) {
                this.emailErrMsg = false
            }
            else {
                this.emailErrMsg = true
            }
        },
        password(value) {
            if (value.length >= 8 && value.length <= 16) {
                this.passwordErrMsg = false;
            }
            else {
                this.passwordErrMsg = true;
            }
        },
    },
    methods: {
        loginFun() {
            if (!this.passwordErrMsg && !this.emailErrMsg) {
                localStorage.setItem('user',this.email)
                this.$router.push({ name: "navigation" });
            } else {
                alert("login failed");
            }
        },
    },
};
</script>

<style scoped>



p{
margin: 0;
padding-bottom: 40px;
color: rgb(168, 71, 71)
}

input[type="email"],
input[type="password"] {
    width: 100%;
    padding: 12px 20px;
    margin: 8px 0;
    border-radius: 5px;
    background-color: #efeff5;
    display: inline-block;
    border: none;
    outline: none;
    border-bottom: 2px solid white;
    box-sizing: border-box;
}
h1{
    text-align: center;
}
button {
    background-color: gray;
    color: black;
    padding: 14px 20px;
    margin: 8px 0;
    border: none;
    cursor: pointer;
    width: 30%;
    border-radius: 90px;
}

button:hover {
    opacity: 0.8;
}

.container {
    padding: 60px;
    
}
.errmsg {
    color: red;
    font-size: 10px;
}
@media screen and (min-width: 780px){
    .box{
        width: 40%;
    }
}
</style>