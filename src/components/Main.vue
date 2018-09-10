<template>
  <div class='main'>
    <h1>{{ title }}</h1>
    <input v-model='text' placeholder='Please Enter text'>

    <h3>Example</h3>
    <CircleType :shape='shape' :text="text"></CircleType>
  </div>
</template>

<script>
  import CircleType from './CircleType'

  export default {
    name: 'Main',
    components: {
      CircleType
    },
    data () {
      return {
        title: 'This is Vue and D3 project for test task',
        text: null,
        shape: [
          {
            bg: '#0001FE'
          },
          {
            x: 150,
            y: 200,
            r: 100
          }
        ]
      }
    }
  }
</script>

<style scoped>
  h1, h2 {
    font-weight: bold;
  }

  h3 {
    color: #000000;
    font-weight: bold;
  }

  input {
    width: 200px;
    height: 40px;
    font-size: 20px;
  }
</style>