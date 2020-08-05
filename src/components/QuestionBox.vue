<template>
  <div>
    <b-jumbotron>
      <template v-slot:lead>Question:</template>
        {{ currentQuestion.question}}
      <hr class="my-4" />
      <b-list-group 
        v-for="(answer,index) in answers" 
        :key="index"
        @click.prevent="selectAnswer(index)"
        :class="[selectedIndex === index ? 'selected':'']"
      >
        <b-list-group-item>{{answer}}</b-list-group-item>
      </b-list-group> 
            <b-button variant="danger" href="#">Clear Choices</b-button>
            <b-button variant="success" href="#">Submit Test</b-button>
            <b-button @click ="next" variant="primary" href="#">Next Question</b-button>
    </b-jumbotron>
  </div>
</template>

<script>
export default {
  props: {
    currentQuestion: Object,
    next: Function
  },
  mounted() {
    console.log(this.currentQuestion)
  },
  data() {
    return {
      selectedIndex: null
    }
  },
  computed: {
    answers() {
      let answers = [...this.currentQuestion.incorrect_answers]
      answers.push(this.currentQuestion.correct_answer)
      return answers
    },
    methods: {
      selectedAnswer(index){
        this.selectedIndex=index
        console.log(index)
      }
    }
  }
};
</script>

<style lang="css" scoped>
.list-group {
  margin-bottom: 15px;
}

.list-group-item:hover {

  background: #ceb4b4;
}
.btn {
  margin: 2px 5px;
  cursor: pointer;
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
