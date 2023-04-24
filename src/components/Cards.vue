<template>
    <div id="main-cards">
        <div class="container-cards">
            <h5>DEPOIMENTOS</h5>
  <h1>Lorem ipsum, dolor sit amet </h1> <br>
<p class="p3">Lorem ipsum dolor sit amet consectetur adipisicing elit.</p>
</div>
<div class="cards">
    <img src="../assets/img/card1.svg" alt="">
    <img src="../assets/img/card2.svg" alt="">
    <img src="../assets/img/card3.svg" alt="">
</div>
</div>



</template>

<script>
export default {
    name: 'Cards',
    
};
</script>

<style lang lang="scss" scoped>
#main-cards{
  
    background: linear-gradient(rgba(255, 255, 255, 0.6),rgba(0,0,0,0.5)), url("../assets/img/cardEdif.svg");
    background-position: 0 -0px;
    background-size: cover;
    height: 100vh;
    padding: 10px;
    background-repeat: no-repeat;
    display: grid;
    align-items: center;
    justify-content: center;
    
}

h5{
    color: red;
    font-size: 15px;
    padding: 15px;
}
h1{
    font-size: 40px;
}



</style>