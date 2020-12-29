<template>
  <div class="wrapper">
    <Score :score="score"/>
    <div class="item-wrapper">
      <div class="items">
        <div class="first-line">
          <Item @choice="click($event)" @cpuChoice="cpuChoice($event)" :item="items[1]" :image="items[1].url" :color="items[1].color"/>
          <Item @choice="click($event)" @cpuChoice="cpuChoice($event)" :item="items[2]" :image="items[2].url" :color="items[2].color"/>
        </div>
        <div class="second-line">
          <Item @choice="click($event)" @cpuChoice="cpuChoice($event)" :item="items[0]" :image="items[0].url" :color="items[0].color"/>
        </div>
      </div>

      <h2 v-if="outcome">{{ outcome }}</h2>

      <Item v-if="computerChoice" :item="computerChoice" :image="computerChoice.url" :color="computerChoice.color" :key="index"/>
      
    </div>
    <button class="restart" @click="restart">Restart</button>
    <NuxtLink to="/"><button>Home</button></NuxtLink>
  </div>
</template>

<script>
export default {
  data(){
    return{
      items: [
      {color: '#E63F3F', item: 'rock', url: require(`../static/icon-rock.svg`)},
      {color: '#3F8DE6', item: 'paper', url: require(`../static/icon-paper.svg`)},
      {color: '#E6A43F', item: 'scissors', url: require(`../static/icon-scissors.svg`)}],
      score: 0,
      playerChoice: '',
      computerChoice: '',
      isPlayerWin: false,
      outcome: '',
      index: 0
    }
  },
  methods: {
    // On player choice
    click(choice){
      this.playerChoice = choice
      this.index += 1
    },
    // On player choice, the CPU make his choice too
    cpuChoice(choice){
      this.computerChoice = this.items[choice]

      if (this.playerChoice === this.items[0] && this.computerChoice === this.items[0]) {
        this.outcome = 'Draw !'
        this.isPlayerWin = false
      } else if (this.playerChoice === this.items[1] && this.computerChoice === this.items[0]) {
        this.outcome = 'You win !'
        this.isPlayerWin = true
        this.score ++
      } else if (this.playerChoice === this.items[2] && this.computerChoice === this.items[0]) {
        this.outcome = 'You lose !'
        this.score --
        this.isPlayerWin = false
      } else if (this.playerChoice === this.items[0] && this.computerChoice === this.items[1]) {
        this.outcome = 'You lose !'
        this.score --
        this.isPlayerWin = false
      } else if (this.playerChoice === this.items[1] && this.computerChoice === this.items[1]) {
        this.outcome = 'Draw !'
        this.isPlayerWin = false
      } else if (this.playerChoice === this.items[2] && this.computerChoice === this.items[1]) {
        this.outcome = 'You win !'
        this.isPlayerWin = true
        this.score ++
      } else if (this.playerChoice === this.items[0] && this.computerChoice === this.items[2]) {
        this.outcome = 'You win !'
        this.score ++
        this.isPlayerWin = true
      } else if (this.playerChoice === this.items[1] && this.computerChoice === this.items[2]) {
        this.outcome = 'You lose !'
        this.score --
        this.isPlayerWin = false
      } else if (this.playerChoice === this.items[2] && this.computerChoice === this.items[2]) {
        this.outcome = 'Draw !'
        this.isPlayerWin = false
      }

    },
    restart(){
      this.computerChoice = ''
      this.playerChoice = ''
      this.outcome = ''
      this.index = 0
      this.score = 0
    }
  }
}
</script>

<style scoped>

  .wrapper{
    height: 100vh;
    width: 100vw;
    display: flex;
    flex-direction: column;
  }

  .item-wrapper{
    display: flex;
    justify-content: space-around;
    align-items: center;
  }

  .first-line{
    width: 100%;
    display: flex;
    justify-content: center;
  }

  .second-line{
    width: 100%;
    display: flex;
    justify-content: center;
  }

  button{
    outline: none;
    height: 60px;
    width: 180px;
    border: 1px solid white;
    border-radius: 10px;
    background-color: transparent;
    color: white;
    cursor: pointer;
    font-weight: bold;
    font-size: 1.1rem;
    bottom: 20px;
    right: 20px;
    position: absolute;
  }

  button:hover{
    color: black;
    background-color: white;
  }

  h2{
    color: white;
  }

  .restart{
    margin-bottom: 75px;
  }

</style>