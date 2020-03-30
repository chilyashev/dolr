<template>
  <v-layout column justify-center align-center>
    <v-flex xs12 sm6 md4 lg4>
      <div class="display-4 font-weight-black text-center">Не!</div>
      <div class="mb-2">
        <p>Ако имаш възможност, остани си вкъщи.</p>
        <p>Липсват ли ти по-простите времена? Кликни <nuxt-link to='/forgotten-times'>тук</nuxt-link>, за да си ги припомниш.</p>
      </div>
      <small> (<a @click='butVisible = !butVisible'>Ама аз съм безсмъртен, млад, здрав, пия ракия, нищо няма да ми стане!</a>)</small>
   
    </v-flex> 
     <v-sheet class="pa-9" elevation="1" v-show='butVisible'>
       Причини да си останеш вкъщи:
       <ol>
         <li>Без трафик към работата!</li>
         <li>Може да заразиш други.</li>
         <li>Може да наваксаш с всичко вкъщи, което отлагаш толкова време. </li>
         <li>Има изследвания, които твърдят, че след прекарване на инфекцията остават белези по белия дроб и са възможни трайни увреждания. Source: <a href="https://www.sciencealert.com/even-those-who-recover-from-corona-can-be-left-gasping-for-breath-afterwards">https://www.sciencealert.com/even-those-who-recover-from-corona-can-be-left-gasping-for-breath-afterwards</a></li>
         <li>Може да намалиш контактите с други хора!</li>
         <li>Може да прекараш всички работни срещи само по бельо<abbr title="Ако забравиш да спреш камерата, ще е забавно за всички">*</abbr>!</li>
         <li>Без трафик към вкъщи!</li>
       </ol>
       
      </v-sheet>
        
  </v-layout>
</template>

<script>
export default {
  components: {},
  data(){
    return {
      butVisible: false
    }
  },
  methods: {

  }
};
</script>
