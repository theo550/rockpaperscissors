<template>
  <div class="container">
    <NuxtLink to="/game"><button>Play</button></NuxtLink>
    <button @click="rulesOn">Rules</button>
    <div @click="rulesOff" class="rules"></div>
  </div>
</template>

<script>
export default {
  data(){
    return{
      isRulesOn: false,
    }
  },
  methods:{
    rulesOn(){
      if (this.isRulesOn === false) {
        document.querySelector('.rules').style.marginTop = '0'
        this.isRulesOn = true
      }
    },
    rulesOff(){
      if (this.isRulesOn === true) {
        document.querySelector('.rules').style.marginTop = '200vh'
        this.isRulesOn = false
      }
    }
  }
}
</script>

<style scoped>

  .container{
    height: 100vh;
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
  }

  button{
    color: white;
    height: 70px;
    width: 250px;
    background-color: transparent;
    border: 1px solid white;
    border-radius: 10px;
    margin: 20px;
    cursor: pointer;
    font-weight: bold;
    font-size: 1rem;
    text-transform: uppercase;
    letter-spacing: 5px;
    outline: none;
  }

  button:hover{
    background-color: #E1E1E1;
    color: black;
  }

  .rules{
    height: 70vh;
    width: 50vw;
    background-color: white;
    background-image: url(../static/image-rules.svg);
    position: absolute;
    background-position: center;
    background-repeat: no-repeat;
    background-size: 70%;
    border-radius: 15px;
    margin-top: 200vh;
    transition: margin-top .4s ease-in-out;
  }

</style>
