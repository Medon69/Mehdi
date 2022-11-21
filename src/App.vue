
<template>
  <div id="app">
    <nav class="navbar-dark bg-dark">
      <router to="" class="text center text-warning" ><CENTER><h1>&#9990; Bienvenue sur votre annuaire &#9990;</h1></CENTER>
      </router>
  <div class="navbar-nav mr-auto">
        <li class="nav-item"> 
          <router-link to="/personnes" class="text center btn btn-primary"><h4>Liste des personnes  
           &#128218; </h4></router-link>
        </li>
        <li class="nav-item">
          <router-link to="ajouter-personne" class="text center btn btn-success"><h4>Ajouter une personne &#128104;</h4></router-link>
        </li>
  </div>
    </nav>
  <div class="container mt-3">
      <router-view />
  </div>
  </div>
</template>


<script>

export default {
  name: "app"
};

</script>
