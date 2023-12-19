<template>
  <div>
    <button v-if="showButton" @click="test" class="generation">Сгенерировать смс код</button>
    <div v-if="showInput">
      <input type="text" v-model="code">
      <button @click="sendCode">Отправить</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data: () => {
    return {
      showButton: true,
      showInput: false,
      code: ''
    }
  },
  methods: {
    test () {
      this.showButton = false
      this.showInput = true
    },
    sendCode () {
      console.log('Отправленный код:', this.code)
    },
    methods: {
      async test () {
        const url = 'http://localhost:3000/sms/create'
        const response = await fetch(url)
        const commits = await response.json()
        console.log(commits)
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.generation {
  background-color: red;
  color: aqua;
  font-size: 32px;
}
.generation:hover {
  cursor: pointer;
   text-decoration: overline
};

</style>
