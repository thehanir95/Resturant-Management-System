<template>
<img class="logo" src="./../assets/1.jpg">
    <h1>Sign Up</h1>
    <div class="register">
        <input type="text" placeholder="Enter Name" />
        <input type="text" placeholder="Enter Email" />
        <input type="password" placeholder="Enter password" />
        <button>Sign Up</button>
    </div>
</template>
<script>
export default{
    name : 'SignUp'
}
</script>

<style>
.logo{
    width: 100px;
}

.register input{
    width: 300px;
    height: 50px;
    padding-left: 200px;
    display: block;
    margin-bottom: 30px;
    margin-right: auto;
    margin-left: auto;
    border: 1px solid skyblue;
}

.register button{
    width: 120px;
    height: 50px;
    border: 1px solid skyblue;
    background: skyblue;
    color: white;
    cursor: pointer;
}
</style>