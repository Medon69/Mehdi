<template>
  <div class="submit-form">
    <div v-if="!submitted">

    
      <div class="form-group">
        <label for="id">id</label>
        <input type="text" class="form-control" id="id"
        v-model= "personne.id"
          />
      </div>
        <div class="form-group">
        <label for="surname">Prénom</label>
        <input type="text" class="form-control" id="surname"
        v-model= "personne.surname"
          />
       </div>
        <div class="form-group">
        <label for="name">Nom</label>
        <input type="text" class="form-control" id="name"
        v-model= "personne.name"
          />
       </div>
       <div class="form-group">
        <label for="phone">Téléphone</label>
        <input type="text" class="form-control" id="phone"
        v-model= "personne.phone"
          />
       </div>
       <div class="form-group">
        <label for="city">Ville</label>
        <input type="text" class="form-control" id="city"
        v-model= "personne.city"
          />
      </div>

      <button @click="creerPersonne" class="btn btn-success">Ajouter</button>
    </div>

    <div v-else>
      <h3>Personne ajoutée avec succès!</h3>
      <button class="btn btn-success" @click="resetForm">Ajouter une nouvelle personne</button>
    </div>
  </div>
</template>

<script>
import PersonneDataService from "../services/PersonneDataService";

export default {
  name: "add-personne",
    data() {
    return {
      personne: {
        id: null,
        name: "",
        surname: "",
        phone: "",
        city: ""
      },
      submitted: false
    };
  },
  methods: {
    creerPersonne() {
      var data = {
        id: this.personne.id,
        name: this.personne.name,
        surname: this.personne.surname,
        phone: this.personne.phone,
        city: this.personne.city,
      };
      
      PersonneDataService.create(data)
      .then(response => {
          console.log(response.data);
          this.$router.push({path:'/personnes'});
          this.submitted = true;
        })
        .catch(e => {
          console.log(e);
      })
    },
    
    resetForm() {
      this.submitted = false;
      this.personne = {};
    }
  }
};
</script>

<style>
.submit-form {
  max-width: 300px;
  margin: auto;
}
</style>
