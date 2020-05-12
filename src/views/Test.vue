<template>
  <div class="test">
    <div class="margin-container"></div>
    <div>
      <h2>Evaluez vos symptômes</h2>
      <form @submit.prevent="getEvaluation">
        <radio-question
          question="Avez-vous une sensation de manque de souffle d'origine brusque? (en absence d'une autre patologie qui justifierait ce symptôme)?"
          name="airShortness"
        ></radio-question>
        <radio-question
          question="Avez-vous la fiebre? (+37.7ºC)"
          name="fever"
        ></radio-question>
        <radio-question
          question="Avez-vous une toux seche et persistante?"
          name="dryCough"
        ></radio-question>
        <radio-question
          question="Avez-vous été en contact avec un patien positif confirmé?"
          name="closeContact"
        ></radio-question>
        <radio-question
          question="Avez-vous de la glaire dans le nez?"
          name="mucus"
        ></radio-question>
        <radio-question
          question="Avez-vous des douleurs musculaires?"
          name="muscularPain"
        ></radio-question>
        <radio-question
          question="Avez-vous des problemes gastro intestinaux?"
          name="gastrointestinal"
        ></radio-question>
        <radio-question
          question="Avez-vous plus de 20 jours avec ces symptômes?"
          name="twentyDays"
        ></radio-question>
        <div class="right">
          <router-link class="back" to="/">Retourner</router-link>
          <button type="submit">
            Obtenir les resultats
          </button>
        </div>
      </form>
    </div>
    <div class="margin-container"></div>
  </div>
</template>

<script>
import RadioQuestion from '@/components/RadioQuestion.vue';

export default {
  name: 'Test',
  components: {
    RadioQuestion
  },
  methods: {
    getEvaluation(submitEvent) {
      const questions = submitEvent.target;
      const scores = {
        airShortness: 60,
        fever: 15,
        dryCough: 15,
        closeContact: 29,
        mucus: 0,
        muscularPain: 0,
        gastrointestinal: 0,
        twentyDays: -15
      };

      const score = Object.keys(scores).reduce((accumulator, scoreName) => {
        return (
          accumulator +
          (questions[scoreName].value === 'true' ? scores[scoreName] : 0)
        );
      }, 0);

      this.$store.commit('filledInTest');
      this.$store.commit('hasSympthoms', score >= 30);
      this.showResults();
    },
    showResults() {
      this.$router.push({
        name: 'Results'
      });
    }
  }
};
</script>

<style>
.test {
  padding-top: 30px;
  display: flex;
  flex-direction: row;
}

.margin-container {
  display: flex;
  width: 15%;
}

.back {
  margin-right: 20px;
}
</style>
