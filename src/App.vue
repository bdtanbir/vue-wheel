<template>
  <div class="wheel_wrap">
    <h1>AuthLab Salami - {{gift}}</h1>
    
    <Wheel
      ref="wheel"
      :gift="gift"
      :data="data"
      @done="done"
      :imgParams="logo"
      @click="spinTheWheel"
    />

    <div class="result-wrapper" v-if="gotValues">
      <div class="result">
      <h1>Congratulations!</h1>
      <h3>You got = {{gotValues.value}}</h3>
      <button type="button" @click="reset()">Done!</button>
    </div>
    </div>
  </div>
</template>

<script>
import { Wheel } from "vue3-fortune-wheel";
import 'vue3-fortune-wheel/dist/library.css'

export default {
  name: "App",
  components: {
    Wheel,
  },
  data() {
    return {
      gift: 11,
      gotValues: false,
      logo: {
        width: 100,
        height: 120,
        src: require('./authlab.jpg'),
        audioSrc: require('./audio.mp3')
      },
      data: [
        {
          id: 1,
          value: "500",
          bgColor: "#7d7db3",
          color: "#ffffff",
        },
        {
          id: 2,
          value: "510",
          bgColor: "#ffffff",
          color: "#000000",
        },
        // {
        //   id: 3,
        //   value: "520",
        //   bgColor: "#1390c9",
        //   color: "#ffffff",
        // },
        {
          id: 4,
          value: "530",
          bgColor: "#7d7db3",
          color: "#ffffff",
        },
        {
          id: 5,
          value: "540",
          bgColor: "#a21d46",
          color: "#ffffff",
        },
        {
          id: 6,
          value: "550",
          bgColor: "#ff60a9",
          color: "#ffffff",
        },
        {
          id: 7,
          value: "560",
          bgColor: "#06c122",
          color: "#ffffff",
        },
        {
          id: 8,
          value: "570",
          bgColor: "#9700a7",
          color: "#ffffff",
        },
        {
          id: 9,
          value: "580",
          bgColor: "#f75432",
          color: "#ffffff",
        },
        {
          id: 10,
          value: "590",
          bgColor: "#f7bd02",
          color: "#ffffff",
        },
        {
          id: 11,
          value: "600",
          bgColor: "#c92729",
          color: "#ffffff",
        },
      ],
    };
  },
  methods: {
    randomGift() {
      return Math.floor(Math.random() * 11) + 1;

      // const values = this.data.map((row) => row.id);
      // return parseInt(Math.random(0, values.length - 1));
      // console.log(reslut_value);
      // return reslut_value;
    },
    done(params) {
      this.gotValues = params;
    },
    spinTheWheel(e) {
      console.log(e);
      // var audio = new Audio('https://themeonfair.cloudaccess.host/themes/audio.mp3');
      // audio.play();
      if (e.shiftKey) {
        this.gift = 11;
      } else {
        this.gift = this.randomGift();
      }
      setTimeout(() => {
        this.$refs.wheel.spin();
      }, 100);
    },
    reset() {
      this.gotValues = false;
      window.location.reload()
    }
  }
};
</script>

<style>
*, *:before, *:after {
  margin: 0;
  padding: 0;
}
body {
  background: #555555 url('./bd-money.webp') center no-repeat;
  background-size: cover;
  position: relative;
}
body:before {
  content: '';
  position: absolute;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  z-index: -1;
  background: #000;
  opacity: 0.7;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.wheel_wrap {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.wheelholder image {
  cursor: pointer;
}
 #wheel svg {
   font-size: 30px;
 }
 .wheel_wrap h1 {
   color: #fff;
   font-size: 35px;
   margin-top: 20px;
 }
 .result-wrapper  {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    display: inline-flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    text-align: center;
    background: rgb(0 0 0 / 65%);

 }
 .result {
    width: 400px;
    height: 400px;
    z-index: 999;
    background: #fff;
    border-radius: 4px;
    display: inline-flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    text-align: center;
}
.result h1 {
  color: #555;
}
.result button {
  margin: 0;
    padding: 6px 11px;
    border-radius: 2px;
    box-shadow: none;
    border: 1px solid #ddd;
    font-size: 16px;
    cursor: pointer;
    margin-top: 14px;
}
</style>
