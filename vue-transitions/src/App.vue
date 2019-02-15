<template>
  <div id="app">
    <div class="toggle toggle--text">
        <input type="checkbox" id="toggle--text" class="toggle--checkbox">
		<label class="toggle--btn" for="toggle--text" data-label-on="Box"  data-label-off="Circle" @click="toggle"></label>
    </div>
    <div class="duration">
        <label for="duration">持续时间（Duration）:</label>
        <input type="range" min="100" max="3000" v-model="duration" id="duration" />
        <span>{{duration}}ms</span>
    </div>
    <FadeTransition mode="out-in" :duration="durationNumber">
        <div key="box" v-if="show" class="box"></div>
        <div key="circle" v-else class="circle"></div>
    </FadeTransition>
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
      duration: 300
    }
  },
  methods: {
    toggle () {
      this.show = !this.show
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
.toggle {
	display: block;
	text-align: center;
	margin-top: 40px;
    margin-bottom: 40px;
    user-select: none;
}
.toggle--checkbox {
    display: none;
}
.toggle--btn {
    display: block;
	margin: 0 auto;
    font-size: 1.4em;
    transition: all 350ms ease-in;
}
.toggle--btn:hover {
	cursor: pointer;
}
.toggle--btn {
    position: relative;
    width: 320px;
    height: 70px;
    text-transform: capitalize;
    font-weight: bold;
    border-radius: 40px;
    border: 1px solid #8c8c8c;
    border-right: 2px solid #8c8c8c;
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
.toggle--btn::before,
.toggle--btn::after {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
}
.toggle--btn::before {
    content: attr(data-label-on);
    left: 15%;
    color: #db4c00;    
}
.toggle--btn::after {
    content: attr(data-label-off);
    right: 15%;
    color: #999;
}
.toggle--checkbox:checked + .toggle--btn {
    border-left: 2px solid #8c8c8c;
    border-right: 1px solid #8c8c8c;
    box-shadow: inset 90px 0 10px rgba(255, 255, 255, 0), inset 3px 3px 18px -2px #8c8c8c, 0 0 15px #ccc, 0px -5px 16px 1px #ddd, -5px -5px 16px 1px #ddd, 5px -5px 16px 1px #ddd, -5px -5px 16px 1px #ddd, 5px -5px 16px 1px #ddd, -17px 9px 0 -5px rgba(255, 255, 255, 0.6), 3px 6px 12px -7px #000, 0 0 0 14px #fff, 0 0 0 15px #999;
}
.toggle--checkbox:checked + .toggle--btn::before {
    color: #999;
}
.toggle--checkbox:checked + .toggle--btn::after {
    color: #db4c00;
}

.box,
.circle {
  width: 200px;
  height: 200px;
  margin: 20px auto;
  background-color: rgb(208, 141, 213);
  box-shadow: rgba(208, 141, 213, 0.5) 0px 6px 20px;
  border-radius: 10px;
}
.circle {
    border-radius: 100%;
    background-color: rgb(59, 99, 202);
    box-shadow: rgba(100, 134, 196, 0.5) 0px 6px 20px;
}
</style>
