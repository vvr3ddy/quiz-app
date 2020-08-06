<template>
  <div class="question-box-container">
    <b-jumbotron>
      <template slot="lead">
        {{ currentQuestion.question }}
      </template>

      <hr class="my-4" />

      <b-list-group>
        <b-list-group-item
          v-for="(answer, index) in answers"
          :key="index"
          @click.prevent="selectAnswer(index)"
          :class="answerClass(index)"
        >
          {{ answer }}
        </b-list-group-item>
      </b-list-group>

      <b-button
        variant="primary"
        @click="submitAnswer"
        :disabled="selectedIndex === null || answered"
      >
        Submit
      </b-button>
      <b-button @click="next" variant="success">
        Next
      </b-button>
    </b-jumbotron>
  </div>
</template>

<script>
import {_} from 'lodash';
export default {
  props: {
    currentQuestion: Object,
    next: Function
  },
  mounted() {
    console.log(this.currentQuestion)
  },
  watch: {
    currentQuestion(){
      this.selectedIndex = null
      this.shuffleAnswers
    }
  },
  data() {
    return {
      selectedIndex: null,
      shuffledAnswers: []
    }
  },
  computed: {
    answers() {
      let answers = [...this.currentQuestion.incorrect_answers]
      answers.push(this.currentQuestion.correct_answer)
      return answers
    },
    methods: {
      selectAnswer(index){
        this.selectedIndex=index
        console.log(index)
      },
      shuffleAnswers() {
        let answers = [...this.currentQuestion.incorrect_answers]
        this.shuffledAnswers = _.shuffle(answers)
      }
    }
  } 
};
</script>


<!--CSS Here-->
<style lang="css" scoped>
.list-group {
  margin-bottom: 15px;
}

.list-group-item:hover {

  background: #b7ceb4;
  cursor: pointer;
}
.btn {
  margin: 2px 5px;
}

.selected {
  background-color: lightblue;
}

.correct {
  background-color: lightgreen;
}

.incorrect {
  background-color: red;
}
</style>
