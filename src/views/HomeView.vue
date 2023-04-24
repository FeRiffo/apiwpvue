<template>
  <div class="main-container">
  <Banner/>
  <Vantagens/>
  <Cards/>

</div>
</template>

<script>
import Vantagens from '../components/Vantagens.vue';
import Banner from '../components/Banner.vue';
import Cards from '../components/Cards.vue';
  export default {
    name: 'Home',
    components:{
    Banner,
    Vantagens,
    Cards
}
  }
</script>
