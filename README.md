# Open COVID19 Test en FR

Un test d'auto evaluation pour le COVID-19 en open source qui donnent les memes resultats que le site [coronamadrid.com](https://www.coronamadrid.com/) sans conserver tes precieux donnees personnelles. La version en FR ici http://linkedvocabs.org/open-covid19-test/ 

Version originale en Castellan (ESP): https://celiavelmar.github.io/open-covid19-test/


### Algorithme


L'algorithme original en FR serait le suivant:

```javascript
var scores = {
  pb_respiratoire: 60,
  fievre: 15,
  toux: 15,
  contact_positif: 29,
  mucosidad: 0,
  doulour_musculaire: 0,
  gastrointestinal: 0,
  plus_de__20_jours: -15
};
var sc = 0;
for (var k in answers) {
  if (answers[k]) {
    sc = sc + scores[k];
  }
}
if (sc >= 30) {
  return 'avec-symptomes';
} else {
  return 'sans-symtomes';
}
```


Les questions et leurs ponctuations en cas de "Oui", sont les suivantes:

- Avez-vous une sensation de manque de souffle d'origine brusque? (en absence d'une autre patologie qui justifierait ce symptome)? **60 points**
- Avez-vous la fiebre? (+37.7ºC) **15 points**
- Avez-vous une toux seche et persistante? **15 points**
- Avez-vous été en contact avec un patien positif confirmé?  **29 points**
- Avez-vous de la glaire dans le nez?  **0 points**
- Avez-vous des douleurs musculaires? **0 points**
- Avez-vous des problemes gastro intestinaux?  **0 points**
- Avez-vous plus de 20 jours avec ces symptômes? **-15 points**

Les explications sur comment cet algorithme fut retrouvé se trouve ici car initialement pas open source:

![Imagen del complejo algoritmo que la aplicación de la Comunidad de Madrid envía en un JSON mediante una petición HTTP GET](public/ComplexAlgorithm.png)

### Note informative et responsabilités

Ce questionnaire a uniquement pour objectif de vous orienter en fonction de votre état de santé et des symptômes que vous déclarez. L’avis qu'il fournit n’a pas de valeur médicale. 

Les données de ce guide orientatif se base sur l'application de la Communauté de Madrid, Espagne en date du 21 mars 2020. 
