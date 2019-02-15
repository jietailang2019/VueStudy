<template>
  <div id="app">
    <div class="toggle toggle--btn" @click="addItem">添加</div>
    <div class="duration">
        <label for="duration">持续时间（Duration）:</label>
        <input type="range" min="100" max="3000" v-model="duration" id="duration" />
        <span>{{duration}}ms</span>
    </div>
    <div class="tips">提示：点击下面的盒子，对应盒子会立即删除</div>
    <div class="wrapper">
        <FadeTransition group :duration="durationNumber">
            <div class="box" v-for="(item, index) in list" @click="remove(index)" :key="item"></div>
        </FadeTransition>
    </div>
  </div>
</template>

<script>
import FadeTransition from './components/FadeTransition'

export default {
  name: 'app',
  components: {
    FadeTransition
  },
  data () {
    return {
      show: true,
      duration: 300,
      list: [1,2,3,4,5]
    }
  },
  methods: {
    toggle () {
      this.show = !this.show
    },
    remove(index) {
        this.list.splice(index, 1)
    },
    addItem() {
        let randomIndex = Math.floor(Math.random() * this.list.length)
        this.list.splice(randomIndex, 0, Math.random())
    }
  },
  computed: {
      durationNumber() {
          return parseInt(this.duration);
      }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

/* default style*/
.toggle--btn {
    position: relative;
    min-width: 160px;
    min-height: 70px;
    margin: 40px auto;
    font-size: 1.4em;
    transition: all 350ms ease-in;
    display: inline-flex;
    justify-content: center;
    align-items: center;
    text-transform: capitalize;
    user-select: none;
    font-weight: bold;
    border-radius: 40px;
    border: 1px solid #8c8c8c;
    box-shadow: 
        inset 90px 0 10px rgba(255, 255, 255, 0.6), 
        inset -3px 3px 18px -2px #8c8c8c, 
        0 0 15px #ccc, 
        0px -5px 16px 1px #ddd, 
        -5px -5px 16px 1px #ddd, 
        5px -5px 16px 1px #ddd, 
        -5px -5px 16px 1px #ddd, 
        5px -5px 16px 1px #ddd, 
        17px 9px 0 -5px rgba(255, 255, 255, 0.6), 
        -3px 6px 12px -7px #000, 
        0 0 0 14px #fff, 
        0 0 0 15px #999;
}
.toggle--btn:hover {
	cursor: pointer;
}
.tips {
    margin: 20px 0 10px;
    font-size: 12px;
    color: red;
    font-style: italic;
}
.wrapper > div {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-wrap: wrap;
}
.box{
  width: 100px;
  height: 100px;
  margin: 10px;
  background-color: rgb(208, 141, 213);
  box-shadow: rgba(208, 141, 213, 0.5) 0px 6px 20px;
  border-radius: 10px;
}

</style>
