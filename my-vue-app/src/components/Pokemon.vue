<template>
      <main role="main" class="container">
        <br/>
        <div class="jumbotron">
          
            <h1>{{store.getters.getCollection[msg].name}}</h1>
            <p><img :src="store.getters.getCollection[msg].sprite"></p>
           <div class="row">
             <div class="col">
               <table class="table">
              <tbody>
                <tr>
                  <th class="text-center">Type(s) :</th>
                  <td v-for="type in store.getters.getCollection[msg].types" :key="type.name">{{type.type.name}}</td>
                </tr>
              </tbody>
            </table>
             </div>
           </div>
            <div class="row">
            <div class="col-6">
            <table class="table">
              <tbody>
                <tr>
                  <th class="text-center">Id :</th>
                  <td>{{store.getters.getCollection[msg].id}}</td>
                </tr>
                <tr>
                  <th class="text-center">Taille :</th>
                  <td>{{store.getters.getCollection[msg].height}}0 cm</td>
                </tr>
                <tr>
                  <th class="text-center">Poids :</th>
                  <td>{{store.getters.getCollection[msg].weight}}0 g</td>
                </tr>
              </tbody>
            </table>
            </div>
            <div class="col-6">
            <table class="table">
              <tbody>
                <tr>
                  <th class="text-center">Genre :</th>
                  <td>{{store.getters.getCollection[msg].genus}}</td>
                </tr>
                <tr>
                  <th class="text-center">Génération :</th>
                  <td>{{store.getters.getCollection[msg].generation.toUpperCase()}}</td>
                </tr>
                <tr>
                  <th class="text-center">Habitat :</th>
                  <td>{{store.getters.getCollection[msg].habitat}}</td>
                </tr>
              </tbody>
            </table>
            </div>
            
            </div>

            <button type="button" class="btn btn-secondary"><router-link to="/accueil">Aller à l'accueil   </router-link></button>
        </div>
    </main>
</template>

<script lang="ts">
import { ref, defineComponent } from 'vue'
import { useStore } from 'vuex'

export default defineComponent({
  setup() {
    const store = useStore()
    const msg = 1;





    return {
      msg,
      store
    };
  },
  created() {
    this.recupId()
  },
  watch: {
    '$route':'recupId'
  },
  methods: {
    recupId () {
      this.msg =  this.$route.params.id -1
    },
    collect () {
        console.log(this.store.getters.getCollection[this.msg])
    },
  }
});
</script>

<style scoped>
</style>