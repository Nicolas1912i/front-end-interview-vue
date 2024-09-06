<script>
export default {
  data() {
    return {
      grid: Array(9).fill(null),
      listPosition: Array(),
      hiddenIndex: [4, 5],
    }
  },
  methods: {
    appendElement(index) {
      this.listPosition.push(index)
      if (this.areAllBoxesGreen()) {
        while (this.listPosition.length > 0) {
          setTimeout(() => {
            console.log(this.listPosition.length)
            this.listPosition.pop()
          }, 2000)
        }
      }
      console.log(this.listPosition)
    },
    areAllBoxesGreen() {
      return this.listPosition.length === 7
    }
  }
}
</script>

<template>
  <!-- <button v-on:click="console.log()">Console info</button> -->
  <div class="grid-container">
    <div v-for="(cell, index) in grid" :key="index"  :class="{'grid-item': (!hiddenIndex.includes(index))}">
      <div class="button-container" >
        <button class="buttonClass" 
        :class="{'seected-grid-item': listPosition.includes(index)}" 
        v-if="!hiddenIndex.includes(index)" 
        v-on:click="appendElement(index);areAllBoxesGreen()"></button>
      </div>
    </div>
  </div>
</template>

<style>

.grid-container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 10px;
  width: 300px;
  margin: 0 auto;
}

.seected-grid-item {
  background-color: green;
}

.button-container {
  width: 100%;
  height: 100%;
  background-color: transparent;
}

.grid-item {
  border: 1px solid;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100px;
}

.buttonClass {
  width: 100%;
  height: 100%;
}

</style>