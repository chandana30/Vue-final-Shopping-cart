<template>
    <div class="main">
        <div id="nav">
<button @click="this.$router.push({ name: 'home' })">Home</button> ||
<button @click="this.$router.push({ name: 'mycart' })">MyCart</button>
        </div>
         <router-view />
    </div>
</template>

<script>
export default {
    name:"navigation",
data() {
    return {
        
    }
},
}
</script>

<style  scoped>
#nav{
    text-align: none;
    
}
main{
    color:black;
}

button{
    background-color:springgreen;
    border: none;
    color: black;
    padding: 10px;
    padding-left: 40px;
    padding-right: 40px;
    text-align: center;
    text-decoration: none;
    font-size: 16px;
    border-radius: 12px;
    cursor: pointer;
}
</style>