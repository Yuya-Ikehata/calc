<template>
  <div class="app">
    <div class="monitor">
      <input type="text" class="monitorInner" v-model="box0" />
    </div>
    <div class="topButton">
      <button class="clinkButton" @click="clear">ac</button>
      <button class="clinkButton" @click="operant('-')">+/-</button>
      <button class="clinkButton" @click="operant('*')">%</button>
      <button class="clinkButton" @click="operant('/')">/</button>
    </div>
    <div class="secondButton">
      <button class="clinkButton" @click="setNumber(7)">7</button>
      <button class="clinkButton" @click="setNumber(8)">8</button>
      <button class="clinkButton" @click="setNumber(9)">9</button>
      <button class="clinkButton" @click="operant('*')">*</button>
    </div>
    <div class="thirdButton">
      <button class="clinkButton" @click="setNumber(4)">4</button>
      <button class="clinkButton" @click="setNumber(5)">5</button>
      <button class="clinkButton" @click="setNumber(6)">6</button>
      <button class="clinkButton" @click="operant('-')">-</button>
    </div>
    <div class="forthButton">
      <button class="clinkButton" @click="setNumber(1)">1</button>
      <button class="clinkButton" @click="setNumber(2)">2</button>
      <button class="clinkButton" @click="setNumber(3)">3</button>
      <button class="clinkButton" @click="operant('+')">+</button>
    </div>
    <div class="fifthButton">
      <button class="clinkButton" @click="setNumber(0)">0</button>
      <button class="clinkButton" @click="setNumber(0)">.</button>
      <!-- 小数点の機能をのちにつける -->
      <button class="clinkButton" @click="getEqual">=</button>
    </div>
  </div>
</template>


<script>
export default {
  data() {
    return {
      box0: 0,
      box1: 0,
      box2: 0,
      box3: 0,
      box4: 0,
    }
  },
  mounted() {},
  methods: {
    operant(o) {
      this.box2 = o
    },
    summary(v) {
      this.calc = v
      if (this.first === 0) {
        this.first = this.math
        this.math = 0
      } else {
        this.second = this.math
      }
    },
    getEqual() {
      if (this.box2 === '+') {
        this.box4 = +this.box1 + +this.box3
        this.box0 = this.box4
      } else if (this.box2 === '-') {
        this.box4 = +this.box1 - +this.box3
        this.box0 = this.box4
      } else if (this.box2 === '*') {
        this.box4 = +this.box1 * +this.box3
        this.box0 = this.box4
      } else if (this.box2 === '/') {
        this.box4 = +this.box1 / +this.box3
        this.box0 = this.box4
      }
    },
    setNumber(i) {
      if (this.box2 !== 0) {
        this.box3 = i
        this.box0 = this.box3
      } else {
        this.box1 = i
        this.box0 = this.box1
      }
    },
    clear() {
      this.box0 = 0
      this.box1 = 0
      this.box2 = 0
      this.box3 = 0
      this.box4 = 0
    },
  },
}
</script>

<style scoped>

.app {
    text-align: center;
}

.monitorInner {
  border: none;
}
</style>