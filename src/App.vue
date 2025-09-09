<template>

  <div class="min-h-screen flex flex-col md:flex-col items-center ">
    
    
    <div class="max-w-7xl w-full">
      <navigations></navigations>
    </div>

    <div class="max-w-7xl w-full grow ">
      <component :is="currentView" />
    </div>

    <div class="w-full">
      <footC></footC>
    </div>

  </div>



</template>



<script>

import Home from './pages/home.vue'
import About from './pages/about.vue';
import Impressum from '/src/pages/impressum.vue';
import Datenschutz from '/src/pages/datenschutz.vue';
import Technical from '/src/pages/technical.vue';
import Methodik from '/src/pages/methodik.vue';


import navigations from '/src/components/navi.vue';
import footC from '/src/components/footer.vue';


const routes = {
    "/": Home,
    "/about": About,
    "/impressum": Impressum,
    "/datenschutz": Datenschutz,
    "/technical": Technical,
    "/methodik": Methodik
}

export default {

  components: {
    navigations,
    footC,
  },

  data() {
    return{
      currentPath: window.location.hash
    }
  },

  computed: {
    currentView(){
        return routes[this.currentPath.slice(1) || '/']
    }
  },


  mounted(){
    let self = this;
    window.addEventListener('hashchange', function(){
      self.currentPath = window.location.hash;
    })
  },

};


</script>
