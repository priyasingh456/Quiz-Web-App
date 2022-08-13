<template>
  <div id="app">
    <HeaderPage 
      :numCorrect="numCorrect"
      :numTotal="numTotal"
    />

    <b-container class="bv-example-row my-5">
      <b-row>
        <b-col sm="6" offset="3">
          <QuestionBox 
            v-if="questions.length"
            :currentQuestion="questions[index]"
            :next="next"
            :increment="increment"
          />
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
import HeaderPage from './components/HeaderPage.vue';
import QuestionBox from './components/QuestionBox.vue';


export default {
    name: "App",
    
    components: { HeaderPage, QuestionBox },

    data(){
      return {
        questions: [],
        index: 0,
        numCorrect: 0,
        numTotal: 0
      }
    },

    methods: {
      next(){
        this.index++;
      },

      increment(isCorrect){
        if(isCorrect){
          this.numCorrect++;
        }
        this.numTotal++;
      }
    },

    mounted: function(){
      fetch('https://opentdb.com/api.php?amount=10&category=18&type=multiple', {
        method: 'get'
      }) 
         .then((response) => {
          return response.json()
         })
         .then((jsonData) => {
          this.questions = jsonData.results;
         })
    }
}
</script>

<style>
#app {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
