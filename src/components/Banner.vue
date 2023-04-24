<template>
    <div id="main-banner">
        <div class="container">
  <h1>Lorem ipsum, dolor sit amet 
    <br>consectetur adipisicing elit<br>consectetur adipisicing elit...</h1> <br>
<p class="p1">Lorem ipsum dolor sit amet consectetur <br> adipisicing elit. Deserunt ea recusandae <br> adipisicing elit. Deserunt ea recusandae</p>
<h6 class="p1 " >Saiba mas </h6>
</div>
<form >
    
    <h5>Ornare ante sapien risus nulla.</h5>
    <div class="input-box"><input type="text" required placeholder="Nome"></div>
    <div class="input-box"><input type="email" required placeholder="e-mail"></div>
    <div class="input-box"><input type="text" required placeholder="Assunto"></div>
    <div class="input-box"><textarea cols='30' rows='10' type="text" required placeholder="Mensagem"></textarea></div>
    <button class="input-box" type="submit">Enviar</button>
    <p>Lorem ipsum dolor, sit amet consectetur adipisicing elit.<br>
         Velit repellat enim animi porro. Numquam quia saepe eius laborum nostrum.</p>
        
</form>
 </div>
</template>

<script>
export default {
    name: 'Banner',
};
</script>

<style lang="scss" scoped>
#main-banner{
    background-image: url("../assets/img/ba1.svg");
    background-position: 0 -630px;
    background-size: cover;
    height: 650px;
    display: flex;
    align-items: center;
    justify-content: flex-start;
}

#main-banner h1{
    text-align: left;
    padding:  0px 70px;

}
 .container  .p1 {
    display: grid ;
    grid-template-columns: repeat(2,50%);
    padding: 20px;
    gap: 10px;
    width: 950px;
    height: 250px;
    margin-left: left;
    text-align: left;
    padding:  0px 70px;
}
#main-banner h6{
    color: red;
    padding:  0px 70px;
    font-size: 18px;
}

form{
    display: flex;
    flex-direction: column;
    text-align: center;
    gap: 10px;
    background-color: rgb(248, 243, 243);
    font-size: 20px;
    padding: 1%;
    margin: 20%;


    
}

.input-box{
    position: flex-direction;

}
.input-box > input{
    width: 85%;
    height: 50px;
    padding: 0 10px;
    
    background: rgb(255, 255, 255);
    border: 3px;
    letter-spacing: 1px;
    
}
.input-box > textarea{
    width: 85%;
    height: 100px;
    background: rgb(255, 255, 255);
    border: 3px;
    letter-spacing: 1px;
    
    

}



form > button {
    background: red;
    color: white;
   padding: 10px;
   width: 100%;
    border: 3px;
    letter-spacing: 1px;
    margin:0px 250px  ;
    width: 85%;
    margin-left: 8%;
    
    
}


</style>