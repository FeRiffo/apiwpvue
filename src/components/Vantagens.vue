<template>
    <div>
        <div id="main-Vantagens">
        <div class="container-Vantagens">
           
  <h1>Facilis dolorum accusamus  eligendi! 
    <br>Esse dolorum veritatis labore iste<br>consectetur adipisicing elit.</h1> <br>
<p class="p2">Lorem ipsum dolor sit amet consectetur <br> adipisicing elit. Deserunt ea recusandae <br> adipisicing elit. Deserunt ea recusandae</p>
<h6 class="p2 "> <img class="check" src="../assets/img/check.svg"> Lorem ipsum dolor sit amet consectetur </h6>
<h6 class="p2 "> <img class="check" src="../assets/img/check.svg"> Lorem ipsum dolor sit amet consectetur </h6>
<h6 class="p2 "> <img class="check" src="../assets/img/check.svg"> Lorem ipsum dolor sit amet consectetur </h6>
<button type="submit">id pulvnar eu mi id</button>
<div class="img-1"><img src="../assets/img/conversa.svg" alt="">
</div>

</div> 
    </div>
</div>

</template>

<script>
export default {
    name: 'Vantagens'
};
</script>

<style lang="scss" scoped>
#main-Vantagens{
  
    display: flex;
    align-items: center;
    justify-content: flex-start;
    height: 650px;
    
}

#main-Vantagens h1{
    text-align: left;
    padding:  5px 200px;

}
 .container-V  .p2 {
    display: flex ;
    grid-template-columns: repeat(2,50%);
    padding: 20px;
    gap: 10px;
    width: 950px;
    height: 250px;
    margin-left: left;
    text-align: left;
    padding:  0px 70px;
}
#main-Vantagens h5{
    color: red;
    padding:  0px 70px;
    margin: 10px;
}

button{
    background: red;
    color: white;
    font-size: 1rem;
    padding: 10px;
    margin: 20px;
    border-radius: 3%;
}

.img-1{
    
    float: right;
    position: absolute;
    left:50%;
    top: 40%;

}

.check{
    padding: 5px;
    margin: 2px;
}

</style>