<template>
<Header />
    <h1>Hello User, Welcome AddResturant page</h1>
    <form class="add">
        <input type="text" name="name" placeholder="Enter Name" v-model="resturants.name">
        <input type="text" name="address" placeholder="Enter Address" v-model="resturants.address">
        <input type="text" name="contact" placeholder="Enter Contact" v-model="resturants.contact">
        <button type="button" v-on:click="addResturant">Add New Resturant</button>
    </form>
</template>

<script>
import Header from './Header.vue'
import axios from 'axios'
export default{
    name:'AddResturant',
    components:{
        Header
    },
    data(){
        return {
            resturants: {
                name : '',
                address : '',
                contact : ''
            }
        }
    },
    methods:{
       async addResturant()
        {
            console.warn(this.resturants)
            const result = await axios.post("http://localhost:3000/resturants",{
                name :this.resturants.name,
                address : this.resturants.address,
                contact : this.resturants.contact
            });
            if(result.status==201)
            {
                this.$router.push({name:'Home'})  
            }
            console.warn("result",result)  
            }
    },

    mounted()
    {
        let user=localStorage.getItem('user-info');
        if(!user)
        {
          this.$router.push({name:'SignUp'})  
        }
    }
}
</script>
