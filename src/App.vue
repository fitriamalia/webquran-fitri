<template>
  <!--Navigation Bar-->
  <nav class="navbar navbar-expand-lg bg-body-tertiary">
    <div class="container-fluid">
      <a class="navbar-brand" href="#">Al-Qur'an</a>
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNavAltMarkup" aria-controls="navbarNavAltMarkup" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNavAltMarkup">
        <div class="navbar-nav">
          <a class="nav-link active" aria-current="page"> <router-link to="/" class="nav-home">Al-Qur'an Indonesia</router-link></a>
          <a class="nav-link"> <router-link to="About" class="nav-surah">Baca Qur'an</router-link></a>
        </div>
      </div>
    </div>
  </nav>

  <!--Router View-->
  <RouterView/>
</template>

<style scoped>

.container-fluid {
  background-color: #282828;
}

.navbar-brand {
  -webkit-text-fill-color: #74a662;
  font-weight: bolder;
}

.nav-surah {
  -webkit-text-fill-color: #74a662;
}


.nav-home {
  -webkit-text-fill-color: #74a662;
}
</style>
