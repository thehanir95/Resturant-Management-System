<template>
<Header />
    <h1>Hello User, Welcome UpdateResturant page</h1>
     <form class="add">
        <input type="text" name="name" placeholder="Enter Name" v-model="resturants.name">
        <input type="text" name="address" placeholder="Enter Address" v-model="resturants.address">
        <input type="text" name="contact" placeholder="Enter Contact" v-model="resturants.contact">
        <button type="button" v-on:click="addResturant">Add New Resturant</button>
    </form>
</template>

<script>
import Header from './Header.vue'
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
