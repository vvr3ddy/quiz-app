<template>
  <div>
    <b-jumbotron>
      <template v-slot:lead>Sample Question</template>

      <hr class="my-4" />

      <div>
        <b-form-group label="Sample Options">
          <b-form-radio v-model="selected" name="some-radios" value="A">Option A</b-form-radio>
          <b-form-radio v-model="selected" name="some-radios" value="B">Option B</b-form-radio>
        </b-form-group>

        <div class="mt-3">
          Your Choice:
          <strong>{{ selected }}</strong>
        </div>
      </div>
      <b-container class="bv-example-row">
        <b-row>
          <b-col sm="2">
            <b-button variant="danger" href="#">Clear Choices</b-button>
          </b-col>
          <b-col sm="2" offset="2">
            <b-button variant="success" href="#">Submit Test</b-button>
          </b-col>
          <b-col sm="2" offset="2">
            <b-button variant="primary" href="#">Next Question</b-button>
          </b-col>
        </b-row>
      </b-container>
    </b-jumbotron>
  </div>
</template>

<script>
export default {
  data() {
    return {
      selected: "",
    };
  },
};
</script>
