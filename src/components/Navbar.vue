<template>
    <div id="nav">
        <RouterLink to="/" id="logo-url"> <img src="../assets/img/logo.svg" id="logo"></RouterLink>
    <router-link to="#">Como funciona</router-link>
    <router-link to="#">Vantages</router-link>
    <router-link to="/Depoimentos">Depimentos</router-link>
    <router-link to="#">Dúvidas</router-link>
    <RouterLink to="#"> <img src="../assets/img/incontel.svg" ></RouterLink>
    <router-link to="#">99 9999-9999</router-link>
    <button type="submit">Lorempppp</button>
  </div>
</template>

<script>

export default {
    name: "Navbar",
    
};
</script>

<style lang="scss" scoped>
#nav{
    background-color: #ffffff;
    border-bottom: 1px solid #2420205e;
    padding:  22px 100px;
    display: flex;
    justify-content: flex-end;
    align-items: center;
}

#nav #logo-url{
    margin: auto;
    margin-left: 0;
    
}
#nav a{
    color: #111;
    text-decoration: none;
    margin: 13px;
    transition: .5s;
}
#nav a:hover{
    color: #5a5959a9;
}

button{
    background: red;
    color: white;
    font-size: 1rem;
    padding: 10px;
    margin: 20px;
    border-radius: 6% 5% 6% 5%;
    transition: .5s;
   

}

</style>