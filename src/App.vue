<template>
  <h1>{{title}}</h1>
  <input type="text" ref="student_name" v-model.lazy="name">
  <button @click="handleClick">Click Me!</button>
  <hr>
  <div v-if="showMyComponent">
    <MyComponent header="my props Header" :student_name="name" @closeMyComponent="toggleMyComponent" />
  </div>
  
  <button @click="toggleMyComponent" v-else>show MyComponent</button>

  <hr>
  <teleport to='#teleport_content'>
    <ComponentWithSlots>
      <p>i'm a Slot</p>

      <!-- named slot -->
      <template v-slot:links>
        <a href="#">sign In</a>
        <a href="#">sign Up</a>
      </template>
    </ComponentWithSlots>
  </teleport>
</template>

<script>
import MyComponent from './components/MyComponent'
import ComponentWithSlots from './components/ComponentWithSlots'

export default {
  name: 'App',
  components: {
    MyComponent,
    ComponentWithSlots
  },
  data() {
    return {
      title: 'My Vue App :)',
      name: 'osama',
      showMyComponent: false
    }
  },
  methods: {
    handleClick(){
      this.$refs.student_name.value = "clicked"
      this.$refs.student_name.classList.add('active')
      this.$refs.student_name.focus()
    },
    toggleMyComponent(){
      this.showMyComponent = !this.showMyComponent
    }
  }
}
</script>

<style>
#app, #teleport_content {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
