<template>
  <div v-for="advice in advices" :key="advice.id" class="square">
   <div class="advice">
    <p>ADVICE #{{ advice.id }}</p>
    <div>
      <h1>{{ advice.advice}}</h1>
    </div>
    <p class="line">''</p>
    <button @click="showAdvices" class="btn"><img src="https://grmbyrn.github.io/advice-generator/images/icon-dice.svg" alt=""></button><br><br>
   </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      advices:[]
    }
  },
  methods: {
    showAdvices() {
      fetch('https://api.adviceslip.com/advice')
      .then(response => response.json())
      .then(result => this.advices = result)
    }
  },
  mounted() {
    this.showAdvices()
  }
}
</script>

<style>
.line::before, .line::after {
    display: inline-block;
    content: "";
    border-top: 0.3rem solid #4F5D74;
    width: 5rem;
    margin: 0 1rem;
    transform: translateY(-3rem);
 }
.line {
  font-size: 5rem;
    color: #53FFAA;
}
h1 {
  color: #CEE3E9;
}
.advice {
transform: translateY(70px);
}
.advice p {
  color: #53FFAA;
}
.square {
  background-color: #313A48;
  box-shadow: 30px 50px 80px rgb(0 0 0 / 10%);
    border-radius: 15px;
}

body {
  background-color: #202733;
  text-align: center;
  justify-content: center;
  display: grid;
  margin-top: 100px;
font-family: Georgia, 'Times New Roman', Times, serif;
}
.btn {
    background-color: #53FFAA;
    border: none;
    padding: 1.25rem;
    border-radius: 50%;
    position: relative;
    top: 2.125rem;
    transform: translateY(-50px);
}
.btn:focus, .btn:hover {
    box-shadow: 0px 0px 40px #53ffaa;
    cursor: pointer;
}
</style>
