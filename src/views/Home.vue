<template>
  <div class="home">
    <div class="margin-container"></div>
    <div>
      <h1>Auto Evaluation Test COVID-19 selon le modèle Madrilain</h1>
      <p class="home-p">
        Un test de auto diagnostique orientatif pour le COVID-19 en open source en FR similaire au 
        <a href="https://www.coronamadrid.com/">coronamadrid.com</a>
        sans conserver des données sensibles.
      </p>
       
      <p class="home-p">
        L'algorithme original en Castellan ici
        <a href="https://github.com/celiavelmar/open-covid19-test"
          >sur GiTHub
          <font-awesome-icon :icon="['fab', 'github']"></font-awesome-icon
        ></a>
        avec le code source dont j'en ai juste fait le fork.
      </p>
      <info-panel
        class="home-info-panel"
        text="L'information obtenue via ce questionnaire ne remplace pas ni pretend substituer en aucun cas, 
		l'avis d'un medecin. Si tu penses avoir des symptômes compatibles avec le COVID-19, 
		entre en contact avec le numero vert de ta ville ou ton pays. "
      ></info-panel>
      <div class="center">
        <router-link to="/test">
          <button>J'ai compris! Je fais le test</button>
        </router-link>
      </div>
    </div>
    <div class="margin-container"></div>
  </div>
</template>

<script>
import InfoPanel from '@/components/InfoPanel.vue';

export default {
  name: 'Home',
  components: {
    InfoPanel
  }
};
</script>

<style>
a {
  color: cornflowerblue;
}

.home {
  padding-top: 30px;
  display: flex;
  flex-direction: row;
}

.home-p {
  padding: 1% 5%;
}

.home-info-panel {
  margin: 1% 5%;
}

.margin-container {
  display: flex;
  width: 20%;
}
</style>
