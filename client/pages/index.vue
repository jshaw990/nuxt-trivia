<template>
<div>
<div>Points {{ totalPoints }}</div>
  <QuestionHolder :trivia="trivia[question]" @confirmedAnswer="confirmedAnswer" />
</div>
</template>

<script>
import { reactive, toRefs } from '@vue/composition-api'

export default {
  name: 'IndexPage',
  setup () {
    const state = reactive({
      completedAll: false,
      question: 0,
      totalPoints: 0,
      trivia: [
        {
          category: 'nhl',
          question: 'What team has won the most stanley cups',
          answers: ['Toronto Maple Leafs', 'Montreal Canadians', 'New York Rangers', 'Detroit Red Wings'],
          correctAnswer: 'Montreal Canadians',
          points: 10
        },
        {
          category: 'nhl',
          question: 'Who is the all-time NHL Points leader',
          answers: ['Wayne Gretzky', 'Bobby Orr', 'Jaromir Jagr', 'Connor McDavid'],
          correctAnswer: 'Wayne Gretzky',
          points: 10
        },
        {
          category: 'nhl',
          question: 'Which of the following teams has not won a Stanley Cup',
          answers: ['New York Rangers', 'Florida Panthers', 'Tampa Bay Lightening', 'Calgary Flames'],
          correctAnswer: 'Florida Panthers',
          points: 10
        }
      ]
    })

    const nextQuestion = () => {
      if (state.question + 1 >= state.trivia.length) {
        state.question = 0
        state.completedAll = true
      } else {
        state.question = ++state.question
      }
    }

    const confirmedAnswer = (payload) => {
      if (payload === state.trivia[state.question].correctAnswer) {
        state.totalPoints = state.totalPoints + state.trivia[state.question].points

        alert('correct')
      } else {
        alert('wrong')
      }

      nextQuestion()
    }

    return {
      confirmedAnswer,
      nextQuestion,
      ...toRefs(state)
    }
  }
}
</script>
