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

<template>
  <div class="app">
    <div class="monitor">
      <input type="text" class="monitorInner" v-model="box0" />
    </div>
    <div class="topButton">
      <button class="clickButton" @click="clear">AC</button>
      <button class="clickButton" @click="operant('-')">+/-</button>
      <button class="clickButton" @click="operant('*')">%</button>
      <button class="clickButton " @click="operant('/')">/</button>
    </div>
    <div class="secondButton">
      <button class="clickButton" @click="setNumber(7)">7</button>
      <button class="clickButton" @click="setNumber(8)">8</button>
      <button class="clickButton" @click="setNumber(9)">9</button>
      <button class="clickButton" @click="operant('*')">*</button>
    </div>
    <div class="thirdButton">
      <button class="clickButton" @click="setNumber(4)">4</button>
      <button class="clickButton" @click="setNumber(5)">5</button>
      <button class="clickButton" @click="setNumber(6)">6</button>
      <button class="clickButton" @click="operant('-')">-</button>
    </div>
    <div class="forthButton">
      <button class="clickButton" @click="setNumber(1)">1</button>
      <button class="clickButton" @click="setNumber(2)">2</button>
      <button class="clickButton" @click="setNumber(3)">3</button>
      <button class="clickButton" @click="operant('+')">+</button>
    </div>
    <div class="fifthButton">
      <button class="clickButton" @click="setNumber(0)">0</button>
      <button class="clickButton" @click="setNumber(0)">.</button>
      <!-- 小数点の機能をのちにつける -->
      <button class="clickButton" @click="getEqual">=</button>
    </div>
  </div>
</template>

<style scoped>

* {
    padding: 0;
    margin: 0;
}

.app {
    width: 360px;
    height: 450px;
    text-align: center;
}

.monitor {
    height: 150px;
}

.monitorInner {
    border: none;

}

.topButton, .secondButton, .thirdButton, .forthButton, .fifthButton {
    display: flex;
    justify-content: space-around;
    padding-bottom: 15px;
}

.clickButton {
    width: 70px;
    height: 70px;
    border: 0;
    border-radius: 50px;
    font-size:25px;
    background-color: #444;
    color: #eee;
    transition-duration: 0.3s;
}

.clickButton:active {
    background-color:#ddd;

}

.fifthButton .clickButton:nth-child(1) {
    width: 160px;
    text-align: left;
}


</style>