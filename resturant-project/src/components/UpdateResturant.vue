<template>
<Header />
    <h1>Hello User, Welcome UpdateResturant page</h1>
     <form class="add">
        <input type="text" name="name" placeholder="Enter Name" v-model="resturants.name">
        <input type="text" name="address" placeholder="Enter Address" v-model="resturants.address">
        <input type="text" name="contact" placeholder="Enter Contact" v-model="resturants.contact">
        <button type="button" v-on:click="updateResturant">Update Resturant</button>
    </form>
</template>

<script>
import Header from './Header.vue'
import axios from 'axios'
export default{
    name:'UpdateResturant',
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
       async updateResturant(){
           console.warn(this.resturants)
            const result = await axios.put("http://localhost:3000/resturants/"+this.$route.params.id,{
                name :this.resturants.name,
                address : this.resturants.address,
                contact : this.resturants.contact
            });
            if(result.status==200)
            {
                this.$router.push({name:'Home'})  
            }
            console.warn("result",result)  
        }
    },
   async mounted()
    {
        let user=localStorage.getItem('user-info');
        if(!user)
        {
          this.$router.push({name:'SignUp'})  
        }
        const result = await axios.get("http://localhost:3000/resturants/"+this.$route.params.id);
        // console.warn(this.$route.param.id)
        console.warn(result.data)
        this.resturants=result.data
    }
}
</script>
