<template>
  <h1>{{title}}</h1>
  <input type="text" ref="student_name" v-model.lazy="name">
  <button @click="handleClick">Click Me!</button>
  <hr>
  <MyComponent header="my props Header" :student_name="name" />
</template>

<script>
import MyComponent from './components/MyComponent'

export default {
  name: 'App',
  components: {
    MyComponent
  },
  data() {
    return {
      title: 'My Vue App :)',
      name: 'osama'
    }
  },
  methods: {
    handleClick(){
      this.$refs.student_name.value = "clicked"
      this.$refs.student_name.classList.add('active')
      this.$refs.student_name.focus()
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
