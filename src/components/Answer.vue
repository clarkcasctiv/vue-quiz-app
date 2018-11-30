<template>
  <div class="alert alert-success text-center">
    <h1>
      That's the correct answer!
      <hr />
      <button class="btn btn-primary" @click="onNextQuestion">
        Next Question
      </button>
    </h1>
  </div>
</template>

<script>
export default {
  methods: {
    onNextQuestion() {
      this.$emit("confirmed");
    }
  }
};
</script>
