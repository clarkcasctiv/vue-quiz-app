<template>
  <div class="container">
    <div class="row">
      <div class="row-sm">
        <h1 class="text-center">The Most Awesome Quiz</h1>
      </div>
    </div>
    <hr />
    <div class="row">
      <div class="row-sm">
        <transition name="flip" mode="out-in">
          <component
            :is="mode"
            @answered="answered($event)"
            @confirmed="mode = 'Question'"
          ></component>
        </transition>
      </div>
    </div>
  </div>
</template>

<script>
import Question from "./components/Question.vue";
import Answer from "./components/Answer.vue";
export default {
  data() {
    return {
      mode: "Question"
    };
  },
  components: {
    Question,
    Answer
  },
  methods: {
    answered(isCorrect) {
      if (isCorrect) {
        this.mode = "Answer";
      } else {
        this.mode = "Question";
        alert("That's the wrong answer! Try Again!");
      }
    }
  }
};
</script>

<style>
.flip-enter-active {
  animation: flip-in 0.5s ease-out forwards;
}
.flip-leave-active {
  animation: flip-out 0.5s ease-out forwards;
}
@keyframes flip-out {
  from {
    transform: rotateY(0deg);
  }
  to {
    transform: rotateY(90deg);
  }
}
@keyframes flip-in {
  from {
    transform: rotateY(90deg);
  }
  to {
    transform: rotateY(0deg);
  }
}
</style>
