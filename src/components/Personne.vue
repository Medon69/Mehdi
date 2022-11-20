<template>
 <div v-if="currentPersonne">
  <div class="col-sm-6">
    <label for="id">ID</label>
    <input type="text" class ="form-control" id="id" name="" v-model="currentPersonne.id"
    /> 
  </div> 
  <div class="col-sm-6">
    <label for="id">Prenom</label>
    <input type="text" class ="form-control" id="id" name="surname" v-model="currentPersonne.surname"
    /> 
  </div> 
  <div class="col-sm-6">
    <label for="id">Nom</label>
    <input type="text" class ="form-control" id="id" name="name" v-model="currentPersonne.name"
    /> 
  </div> 
  <div class="col-sm-6">
    <label for="id">Telephone</label>
    <input type="text" class ="form-control" id="id" name="phone" v-model="currentPersonne.phone"
    /> 
  </div> 
  <div class="col-sm-6">
    <label for="id">Ville</label>
  <input type="text" class ="form-control" id="id" name= "city" v-model="currentPersonne.city"
    /> 

  </div>

    <button class="btn btn-danger col-sm-3"
      @click="deletePersonne"

    >
      Supprimer
    </button>

    <button type="submit" class="btn btn-warning col-sm-3"
      @click="updatePersonne"
    >
      Modifier
    </button>
    <p>{{ message }}</p>
   </div> 
 </template>

<script>
import PersonneDataService from "../services/PersonneDataService";

export default {
  name: "personne",
  data() {
    return {
      currentPersonne: null,
      message: ''
    };
  },
  
 methods: { 
  getPersonne(id) {
      PersonneDataService.get(id)
        .then(response => {
          this.currentPersonne = response.data;
          console.log(response.data);
        })
        .catch(e => {
          console.log(e);
        });
    },

  updatePersonne() {
     PersonneDataService.update(this.currentPersonne)
        .then(response => {
          
          this.message = 'Personne modifiée avec succès!';
          console.log(response.data);
          this.submitted = true;
        })
        .catch(e => {
          console.log(e);
        });
    },

  deletePersonne() {
     PersonneDataService.delete(this.currentPersonne.id)
        .then(response => {
          this.currentPersonne= response.data;
          console.log(response.data);
          this.$router.push({path:'/personnes'});
           })
         .catch(e => {
          console.log(e);
         })
        .catch(e => {
          console.log(e);
         });
     },

   },

  mounted() {
    this.message = '';
    this.getPersonne(this.$route.params.id);
  }
}

</script>

 <style>
  .edit-form {
    max-width: 300px;
    margin: auto;
}
 </style>

