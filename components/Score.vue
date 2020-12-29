<template>
  <div class="score-wrapper">
    <div class="text">
      <h1>Rock</h1>
      <h1>Paper</h1>
      <h1>Scissors</h1>
    </div>
    <div class="score">
      <p>score</p>
      <h1>{{ score }}</h1>
    </div>
  </div>
</template>

<script>
export default {
  props: ['score'],
}
</script>

<style scoped>
  .score-wrapper{
    height: 150px;
    width: 60%;
    color: white;
    display: flex;
    justify-content: space-between;
    align-items: center;
    border: 1px solid rgb(190, 190, 190);
    border-radius: 15px;
    margin: 30px auto;
  }

  .text{
    margin-left: 40px;
    text-transform: uppercase;
  }

  .score{
    height: 80%;
    width: 20%;
    background-color: white;
    border-radius: 20px;
    margin-right: 20px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    color: #4A4A4A;
  }

  .score p{
    letter-spacing: 5px;
  }

  .score h1{
    font-size: 3rem;
  }

  .container h1{
    text-transform: uppercase;
  }
</style>