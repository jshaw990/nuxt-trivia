<template>
  <div class="d-flex flex-column justify-center align-center">
    {{ trivia.question }}
    <div
      v-for="option in trivia.answers"
      :key="option.index"
      class="my-4"
    >
      <v-chip
        :color="selectedAnswer === option ? 'yellow lighten-3' : 'white'"
        text-color="black"
        @click="selected(option)"
      >
        {{ option }}
      </v-chip>
    </div>
    <v-btn
      v-if="selectedAnswer !== ''"
      xlarge
      color="success"
      width="250px"
      class="mt-6 mb-12"
      @click="confirmAnswer"
    >
      Continue
    </v-btn>
  </div>
</template>

<script>
import { reactive, toRefs } from '@vue/composition-api'

export default {
  name: 'QuestionHolder',
  props: {
    trivia: {
      type: Object,
      required: true
    }
  },
  setup (props, context) {
    const state = reactive({
      selectedAnswer: ''
    })

    const selected = (option) => {
      state.selectedAnswer = option
    }

    const confirmAnswer = () => {
    const selected = state.selectedAnswer
      context.emit('confirmedAnswer', selected)
      state.selectedAnswer = ''
    }

    return {
      selected,
      confirmAnswer,
      ...toRefs(state)
    }
  }
}
</script>
