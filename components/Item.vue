<template>
    <div @click="click" :style="{borderColor: border}" class="item">
      <img :src='img' alt="">
    </div>
</template>

<script>
export default {
  props:['color', 'image', 'item'],
  data(){
    return{
      border: this.color,
      img: this.image
    }
  },
  methods: {
    click(){
      this.$emit('choice', this.item )
      this.$emit('cpuChoice', Math.floor(Math.random() * (2 + 1)))
    }
  }
}
</script>

<style scoped>

  .item{
    height: 150px;
    width: 150px;
    border-radius: 50%;
    background-color: white;
    border: 15px solid red;
    cursor: pointer;
    margin: 30px 60px;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  img{
    z-index: 99;
  }

  .item:hover{
    background-color: #E1E1E1;
  }

</style>