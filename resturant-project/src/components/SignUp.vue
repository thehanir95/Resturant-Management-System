<template>
<img class="logo" src="./../assets/1.jpg">
    <h1>Sign Up</h1>
    <div class="register">
        <input type="text" v-model="name" placeholder="Enter Name" />
        <input type="text" v-model="email" placeholder="Enter Email" />
        <input type="password" v-model="password" placeholder="Enter password" />
        <button v-on:click="signup">Sign Up</button>
        <p>
            <router-link to="/login">Login</router-link>
        </p>
    </div>
</template>
<script>
import axios from 'axios'
export default{
    name : 'SignUp',
    data()
    {
        return {
            name:'',
            email:'',
            password:''
        }
    },
    methods:{
       async signup()
        {
           let result = await axios.post("http://localhost:3000/users",{
               email:this.email,
               password:this.password,
               name:this.name
           });
           console.warn(result);
           if(result.status==201)
           {
            //    alert("signup done");
               localStorage.setItem("use-info",JSON.stringify(result.data))
               this.$router.push({name:'Home'})
           }
        }
    },
    mounted()
    {
        let user=localStorage.getItem('user-info');
        if(user)
        {
          this.$router.push({name:'Home'})  
        }
    }

}
</script>

