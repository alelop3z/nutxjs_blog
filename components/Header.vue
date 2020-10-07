<template>
  <header class="header text-center">	    
    <h1 class="blog-name pt-lg-4 mb-0">
      <nuxt-link to="/">Alejandro Lopez</nuxt-link>
    </h1>
      
    <nav class="navbar navbar-expand-lg navbar-dark" >    
      <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navigation" aria-controls="navigation" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
      </button>

      <div id="navigation" class="collapse navbar-collapse flex-column" >
        <div class="profile-section pt-3 pt-lg-0">
          <img class="profile-image mb-3 rounded-circle mx-auto" src="assets/images/profile.png" alt="image" >			
          
          <div class="bio mb-3">
            Hola, me llamo Alejandro Lopez y me dedico al mundo de la programación web. <br>
            <!-- <nuxt-link to="/about" title="Sobre mí">¿Quieres saber más de mi?</nuxt-link> !-->
          </div><!--//bio-->
          <SocialLinks />
          <hr> 
        </div><!--//profile-section-->
        
        <!-- <ul class="navbar-nav flex-column text-left">
          <li class="nav-item active">
            <nuxt-link to="/" class="nav-link"><i class="fas fa-home fa-fw mr-2"></i> Inicio</nuxt-link>
          </li>
          <li class="nav-item">
            <nuxt-link to="/cv" class="nav-link"><i class="fas fa-file-alt fa-fw mr-2"></i> Mi CV</nuxt-link>
          </li>
          <li class="nav-item">
            <nuxt-link to="/about" class="nav-link"><i class="fas fa-user fa-fw mr-2"></i> Sobre mí</nuxt-link>
          </li>
        </ul> -->
      </div>
    </nav>
  </header>
</template>