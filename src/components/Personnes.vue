<template>
  
  <ul>
    <h3 class="card text-warning bg-dark mb-3 setActivePersonne"
      :class="{ active: id == currentIndex }"
      v-for="(personne, id) in personnes"
      :key="id"
      @click="setActivePersonne(personne, id)"
    >
      {{ personne.surname }} {{ personne.name }} &#9990;

    </h3>
  </ul>

  <div v-if="currentPersonne " >
    {{ currentPersonne.name }}
    {{ currentPersonne.surname }}
    {{ currentPersonne.phone }}
    {{ currentPersonne.city }}

    
  
   <router-link :to="'/personnes/' + currentPersonne.id" class="btn btn-warning">Modifier</router-link>
    
     </div>
     <div v-else>
    <br />
    <p class="btn btn-warning btn-lg btn-block"><h3>Cliquez sur une des personnes pour afficher les détails</h3></p>
   </div>

</template>

<script>
import PersonneDataService from "../services/PersonneDataService";

export default {
  name: "personnes",
  data() {
    return {
      personnes: [],
      currentPersonne: null,
      currentIndex: -1,
    };
  },
  methods: {
    getPersonnes() {
      PersonneDataService.getAll()
        .then(response => {
          this.personnes = response.data;
          console.log(response.data);
        })
        .catch(e => {
          console.log(e);
        });
    },

    setActivePersonne(personne, index) {
      this.currentPersonne = personne;
      this.currentIndex = personne ? index : -1;
    },
  },
  mounted() {
    this.getPersonnes();
  }
};
</script>
