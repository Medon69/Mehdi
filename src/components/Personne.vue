<template>
 <div v-if="currentPersonne">
  <div class="form-group">
    <label for="id">ID</label>
    <input type="text" class ="" id="id" name=""
    v-model="currentPersonne.id"
    /> 
  </div> 
  <div class="form-group">
    <label for="id">Prenom</label>
    <input type="text" class ="" id="id" name="surname"
    v-model="currentPersonne.surname"
    /> 
  </div> 
  <div class="form-group">
    <label for="id">Nom</label>
    <input type="text" class ="" id="id" name="name"
    v-model="currentPersonne.name"
    /> 
  </div> 
  <div class="form-group">
    <label for="id">Telephone</label>
    <input type="text" class ="" id="id" name="phone"
    v-model="currentPersonne.phone"
    /> 
  </div> 
  <div class="form-group">
    <label for="id">Ville</label>
  <input type="text" class ="" id="id" name= "city"
    v-model="currentPersonne.city"
    /> 

  </div> 

    <!-- A INCLURE DANS LE FORM -->
    <button class="badge badge-danger mr-2"
      @click="deletePersonne"
    >
      Supprimer
    </button>


    <!-- A INCLURE DANS LE FORM -->
    <button type="submit" class="badge badge-success"
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
          this.currentPersonne= response.data;
          console.log(response.data);
          this.$router.push({path:'/personnes'});
          this.message = 'Personne modifiée avec succès!';
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
  max-width: 600px;
  margin: auto;
}
 </style>
 <body style="background-color:powderblue;">

<h1>This is a heading</h1>
<p>This is a paragraph.</p>

</body>
