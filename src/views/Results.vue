<template>
  <div class="results">
    <div class="margin-container"></div>
    <div v-if="filledInTest" class="main-container">
      <h2>Résultats</h2>
      <div v-if="hasSympthoms">
        <p>
          Vos réponses suggèrent que vous avez la possibilité d'avoir des symptômes compatible avec le COVID-19 selon l'algorithme de coronamadrid.com.  
        </p>
        <p>
          Quelques recommandations si vous pensez avoir le COVID-19:
        </p>
        <ul>
          <li>
            Surveillez votre évolution et si vos symptômes s'aggravent, surtout si
            vous avez des difficultés respiratoires, contactez le téléphone
            mis en place par votre ville/pays pour le suivi des soins pour COVID-19. 
          </li>
          <li>
            Restez chez vous pour éviter des contagions.
          </li>
          <li>
            Utiliser un masque de protection (en prenant soin de les changer chaque 24h).
          </li>
          <li>
			Si vous vivez avec d'autres personnes, séjournez dans une pièce séparée avec la porte fermée et utilisez votre propre salle de bain dans la mesure du possible.
			Aérez la pièce en évitant les courants vers le reste de la maison. Ne partagez pas la vaisselle, les serviettes ou les draps.
          </li>
          <li>
            Nettoyer les surfaces et objets avec eau de Javel ou des produits désinfectants. 
          </li>
          <li>
            Gardez vos  vêtements sales dans un sac fermé et les laver séparément avec les températures entre 60-90º. 
          </li>
          <li>
            Jetez vos déchets séparément à l'aide d'un contenant avec un couvercle.
          </li>
        </ul>
        <p>
         COVID-19 se transmet par des gouttelettes qui sont expulsées par la toux ou éternuements, donc l’hygiène et l’évitement des contacts par des gestes barrières sont fondamentaux pour réduire la contagion. </p>
      </div>
      <div v-else>
        <p>
          Vos réponses suggèrent que vous n'avez pas des symptômes ou sont insuffisants pour déterminer une contagion au COVID-19 selon l'algorithme de coronamadrid.com.  
        </p>
      </div>
      <info-panel
        text="L'information obtenue via ce questionnaire ne remplace pas ni pretend substituer en aucun cas, 
		l'avis d'un medecin. Si tu penses avoir des symptômes compatibles avec le COVID-19, 
		entre en contact avec le numero vert de ta ville ou ton pays."
      ></info-panel>
      <h3>Quelques liens utiles</h3>
      <a
        href="https://www.gouvernement.fr/info-coronavirus"
        target="_blank"
      >
        Web del Gouvernement Francais avec des informations sur le COVID-19
      </a>
      <br /><br />
      <a
        href="https://solidarites-sante.gouv.fr/soins-et-maladies/maladies/maladies-infectieuses/coronavirus/tout-savoir-sur-le-covid-19/article/reponses-a-vos-questions-sur-le-covid-19-par-des-medecins"
        target="_blank"
      >
        FAQ sur le COVID-19
      </a>
      <br /><br />
      <a
        href="https://www.minsante.cm/site/?q=fr/epid-mie-de-coronavirus-covid---19-"
        target="_blank"
      >
        Informations du Ministere de la Sante au Cameroun sur la situation du COVID-19
      </a>
      <br /><br />
      <a href="https://www.who.int/fr/health-topics/coronavirus/coronavirus" target="_blank">
        Web de l'Organisation Mondiale de la Santé sur le Coronavirus
      </a>
      <div>
        <router-link to="/test">
          <button>Refaire le test</button>
        </router-link>
      </div>
    </div>
    <div class="margin-container"></div>
  </div>
</template>

<script>
import InfoPanel from '@/components/InfoPanel.vue';

export default {
  name: 'Results',
  components: {
    InfoPanel
  },
  computed: {
    filledInTest() {
      return this.$store.state.filledInTest;
    },
    hasSympthoms() {
      return this.$store.state.hasSympthoms;
    }
  },
  created: function() {
    if (!this.filledInTest) {
      this.$router.push({
        name: 'Home'
      });
    }
  }
};
</script>

<style>
.results {
  padding-top: 30px;
  display: flex;
  flex-direction: row;
}

.margin-container {
  width: 15%;
}

.main-container {
  width: 70%;
}

.disclaimer {
  border-radius: 12px;
  border: 1px solid cornflowerblue;
}
</style>
