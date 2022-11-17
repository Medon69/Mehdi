<template>
  <div id="app">
    <nav class="navbar navbar-expand navbar-dark bg-primary">
      <router-link to="" class="navbar-brand"><h3>Bienvenue sur votre annuaire</h3></router-link>
      <div class="navbar-nav mr-auto">
        <li class="nav-item">
          <router-link to="/personnes" class="nav-link"><h4>Personnes</h4></router-link>
        </li>
        <li class="nav-item">
          <router-link to="ajouter-personne" class="nav-link"><h4>Ajouter</h4></router-link>
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
