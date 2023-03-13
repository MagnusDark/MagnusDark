<script>
export default {
  data() {
    return {
      storage: 444,
      transfer: 444,
      backblaze: 0,
      bunnySsd: 0,
      bunnyHdd: 0,
      scalewayMulti: 0,
      scalewaySingle: 0,
      vultr: 0,
      ssd: true,
      hdd: false,
      multi: true,
      single: false,
      windowWidth: 0,
      blue: false,
      red: true,
      yelow: false,
      greenbackblaze: false,
      greenbunnySsd: false,
      greenbunnyHdd: false,
      greenscalewayMulti: false,
      greenscalewaySingle: false,
      greenvultr: false,
      redbackblaze: false,
      redbunnySsd: false,
      redbunnyHdd: false,
      redscalewayMulti: false,
      redscalewaySingle: false,
      redvultr: false,

      max: 0,
      min: 0,
    };
  },
  components: {},
  created() {},
  methods: {
    max1() {
      this.max = Math.max(
        this.scalewayMulti,
        this.scalewaySingle,
        this.vultr,
        this.backblaze,
        this.bunnyHdd,
        this.bunnySsd
      );
      console.log(this.max);
    },
    multi1() {
      this.multi = true;
      this.single = false;
    },
    single1() {
      this.multi = false;
      this.single = true;
    },
    ssd1() {
      this.ssd = true;
      this.hdd = false;
      console.log(this.ssd);
    },

    hdd1() {
      this.hdd = true;
      this.ssd = false;
      console.log(this.hdd);
    },
    changeStorage(value) {
      this.storage = value;
      this.width = this.storage;
    },
    changeTransfer(value) {
      this.transfer = value;
    },
  },
  computed: {
    maxMax() {
      let f = Math.min(
        this.scalewayMulti,
        this.scalewaySingle,
        this.vultr,
        this.backblaze,
        this.bunnyHdd,
        this.bunnySsd
      );
      return f;
    },
    colorMax(){
      this.min = Math.min(
        this.scalewayMulti,
        this.scalewaySingle,
        this.vultr,
        this.backblaze,
        this.bunnyHdd,
        this.bunnySsd
      );

      if (this.scalewayMulti === this.min) {
        this.greenscalewayMulti = true;
      } else {
        this.greenscalewayMulti = false;
      }
      //1
      if (this.scalewaySingle === this.min) {
        this.greenscalewaySingle = true;
      } else {
        this.greenscalewaySingle = false;
      }
      //2
      if (this.vultr === this.min) {
        this.greenvultr = true;
      } else {
        this.greenvultr = false;
      }
      //3
      if (this.backblaze === this.min) {
        this.greenbackblaze = true;
      } else {
        this.greenbackblaze = false;
      }
      //4
      if (this.bunnyHdd === this.min) {
        this.greenbunnyHdd = true;
      } else {
        this.greenbunnyHdd = false;
      }
      // 5
      if (this.bunnySsd === this.min) {
        this.greenbunnySsd = true;
      } else {
        this.greenbunnySsd = false;
      }
      // 6
    },
    colorMin() {
      this.max = Math.max(
        this.scalewayMulti,
        this.scalewaySingle,
        this.vultr,
        this.backblaze,
        this.bunnyHdd,
        this.bunnySsd
      );

      if (this.scalewayMulti === this.max) {
        this.redscalewayMulti = true;
      } else {
        this.redscalewayMulti = false;
      }
      //1
      if (this.scalewaySingle === this.max) {
        this.redscalewaySingle = true;
      } else {
        this.redscalewaySingle = false;
      }
      //2
      if (this.vultr === this.max) {
        this.redvultr = true;
      } else {
        this.redvultr = false;
      }
      //3
      if (this.backblaze === this.max) {
        this.redbackblaze = true;
      } else {
        this.redbackblaze = false;
      }
      //4
      if (this.bunnyHdd === this.max) {
        this.redbunnyHdd = true;
      } else {
        this.redbunnyHdd = false;
      }
      // 5
      if (this.bunnySsd === this.max) {
        this.redbunnySsd = true;
      } else {
        this.redbunnySsd = false;
      }
      // 6

      // if (this.bunnyHdd === this.vultr) {
      //   this.redbunnyHdd = this.redvultr;
      //   this.greenbunnyHdd = this.greenvultr;
      // }
    },
    // colorGreen(){
    //   if (
    //     this.backblaze >
    //     Math.max(
    //       this.scalewayMulti,
    //       this.scalewaySingle,
    //       this.vultr,
    //       // this.backblaze,
    //       this.bunnyHdd,
    //       this.bunnySsd
    //     )
    //   ) {
    //     this.greenbackblaze = true
    //     console.log('qw1232', greenbackblaze)
    //     return true
    //   }

    // },
    window() {
      this.windowWidth = window.screen.width;
      return this.windowWidth;
    },
    first() {
      if (this.storage * 0.005 + this.transfer * 0.01 < 7) {
        this.backblaze = 7;
      } else {
        this.backblaze = this.storage * 0.005 + this.transfer * 0.01;
      }
    },
    secondHdd() {
      if (this.storage * 0.01 + this.transfer * 0.01 > 10) {
        this.bunnyHdd = 10;
      } else {
        this.bunnyHdd = this.storage * 0.01 + this.transfer * 0.01;
      }
    },
    secondSsd() {
      if (this.storage * 0.02 + this.transfer * 0.01 > 10) {
        this.bunnySsd = 10;
      } else {
        this.bunnySsd = this.storage * 0.02 + this.transfer * 0.01;
      }
    },
    thirdMulti() {
      if (this.storage < 75) {
        this.storageCost = 0;
      } else {
        this.storageCost = 0.06;
      }
      if (this.transfer < 75) {
        this.transferCost = 0;
      } else {
        this.transferCost = 0.02;
      }
      this.scalewayMulti =
        (this.storage - 75) * this.storageCost +
        (this.transfer - 75) * this.transferCost;
    },
    thirdSingle() {
      if (this.storage < 75) {
        this.storageCost = 0;
      } else {
        this.storageCost = 0.03;
      }
      if (this.transfer < 75) {
        this.transferCost = 0;
      } else {
        this.transferCost = 0.02;
      }
      this.scalewaySingle =
        (this.storage - 75) * this.storageCost +
        (this.transfer - 75) * this.transferCost;
    },
    four() {
      if (this.storage * 0.01 + this.transfer * 0.01 < 5) {
        this.vultr = 5;
      } else {
        this.vultr = this.storage * 0.01 + this.transfer * 0.01;
      }
    },
  },
};
</script>

<template>
  <div class="main">
    <div class="contols">
      <div class="storage">
        <div class="slidecontainer">
          <div class="min">0GB</div>
          <input
            type="range"
            min="1"
            max="1000"
            class="slider"
            id="myRange"
            @change="color"
            v-model="transfer"
          />
          <div class="max">1000GB</div>
          <div class="value">Transfer:{{ this.transfer }}</div>
        </div>
      </div>
      <div class="transfer">
        <div class="slidecontainer">
          <div class="min">0GB</div>
          <input
            type="range"
            min="1"
            max="1000"
            class="slider"
            id="myRange"
            v-model="storage"
          />
          <div class="max">1000GB</div>
          <div class="value">Storage:{{ this.storage }}</div>
        </div>
      </div>
    </div>

    <!-- <button class="btn" @click="max1">NAZHMI</button>
    <div class="ddd">{{ maxMax }}</div> -->

    <!-- /////result -->
    <div class="result" v-if="`{{window > 480}}`">
      <!-- 1 -->
      <div class="backblaze">
        <div class="name">
          <img class="img" src="./img/blackblaze.png" />
        </div>
        <div class="line">
          <div
            :class="{ green: greenbackblaze, red: redbackblaze }"
            class="dinamicResultbackblaze"
            :style="{ width: backblaze * 10 + 'px' }"
          ></div>
          <div class="sum">{{ backblaze.toFixed(2) }} $</div>
        </div>
      </div>

      <!-- 2 -->
      <div class="bunny">
        <div class="name"><img class="img" src="./img/bunny.png" /></div>
        <div class="buttons">
          <div class="hdd btn" @click="hdd1" :class="{ activeBtn: hdd }">
            hdd
          </div>
          <div class="ssd btn" @click="ssd1" :class="{ activeBtn: ssd }">
            ssd
          </div>
        </div>
        <div class="line" v-if="hdd">
          <div
            :class="{ green: greenbunnyHdd, red: redbunnyHdd }"
            class="dinamicResultbunny"
            :style="{ width: bunnyHdd * 10 + 'px' }"
          ></div>
          <div class="sum">{{ bunnyHdd.toFixed(2) }}$</div>
        </div>
        <div class="line" v-if="ssd">
          <div
            :class="{ green: greenbunnySsd, red: redbunnySsd }"
            class="dinamicResultbunny"
            :style="{ width: bunnySsd * 10 + 'px' }"
          ></div>
          <div class="sum">{{ bunnySsd.toFixed(2) }}$</div>
        </div>
      </div>
      <!-- 3 -->
      <div class="scaleway">
        <div class="name">
          <img class="img" src="./img/scaleway.png" />
        </div>
        <div class="buttons">
          <div class="hdd btn" @click="multi1" :class="{ activeBtn: multi }">
            multi
          </div>
          <div class="ssd btn" @click="single1" :class="{ activeBtn: single }">
            single
          </div>
        </div>
        <div class="line" v-if="multi">
          <div
            :class="{ green: greenscalewayMulti, red: redscalewayMulti }"
            class="dinamicResultscaleway"
            :style="{ width: scalewayMulti * 10 + 'px' }"
          ></div>
          <div class="sum">{{ scalewayMulti.toFixed(2) }}$</div>
        </div>
        <div class="line" v-if="single">
          <div
            :class="{ green: greenscalewaySingle, red: redscalewaySingle }"
            class="dinamicResultscaleway"
            :style="{ width: scalewaySingle * 10 + 'px' }"
          ></div>
          <div class="sum">{{ scalewaySingle.toFixed(2) }}$</div>
        </div>
      </div>
      <!-- 4 -->
      <div class="vultr">
        <div class="name"><img class="img" src="./img/vultr.png" /></div>
        <div class="line">
          <div
            :class="{ green: greenvultr, red: redvultr }"
            class="dinamicResultvultr"
            :style="{ width: vultr * 10 + 'px' }"
          ></div>
          <div class="sum">{{ this.vultr.toFixed(2) }}$</div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.btn {
  cursor: pointer;
  font-size: 18px;
  color: antiquewhite;
  border-radius: 3px;
  height: 20px;
  margin-left: 50px;
}
.activeBtn {
  color: #000;
  background: #ffffff;
}
.sum {
  min-width: 70px;
  height: 40px;
  background: #37ff00;
  font-size: 24px;
  padding: 8px;
  border-radius: 3px;
  margin-left: 5px;
}
.img {
  width: 90px;
  height: 40px;
  border-radius: 10px;
}
.line {
  position: absolute;
  left: 200px;
  display: flex;
}
.first {
  -webkit-appearance: none;
  background: #000;
  height: 20px;
  overflow: visible;
  border: 1px solid #000;
}
.slider {
  /* margin: 50px; */
  /* height: 20px; */
  width: 500px;
  /* border: 1px solid #000; */
}

.slidecontainer {
  text-align: center;
  display: flex;
}
.value {
  height: 40px;
  width: 150px;
  border-radius: 5px;
  background: #dbdbdb;
  padding: 10px;
  font-size: 22px;
  /* border: 1px solid #000; */
  margin: 20px;
}
.result {
  margin: 20px;
  border-radius: 10px;
  background: #b0b0b0;
  width: 1080px;
  padding: 10px;
  display: flex;
  flex-direction: column;
}
.dinamicResultbackblaze {
  height: 40px;
  background: rgb(213, 213, 214);
  border-radius: 3px;
  max-width: 800px;
}
.dinamicResultbunny {
  height: 40px;
  background: rgb(213, 213, 214);
  border-radius: 3px;
  max-width: 800px;
}
.dinamicResultscaleway {
  height: 40px;
  background: rgb(213, 213, 214);
  border-radius: 3px;
  max-width: 800px;
}
.dinamicResultvultr {
  height: 40px;
  background: rgb(213, 213, 214);
  border-radius: 3px;
  max-width: 800px;
}

.backblaze {
  margin: 10px;
  display: flex;
}
.bunny {
  margin: 10px;
  display: flex;
}
.scaleway {
  margin: 10px;
  display: flex;
}
.vultr {
  margin: 10px;
  display: flex;
}
.name {
  /* transform: rotate(90deg); */
  width: 50px;
  font-size: 22px;
}
.max {
  font-size: 18px;
  display: flex;
  align-items: center;
}
.min {
  font-size: 18px;
  display: flex;
  align-items: center;
}
.green {
  background: #4dff00;
}
.red {
  background: rgb(255, 0, 0);
}

@media (max-width: 480px) {
  .contols {
    border: 1px solid #000;
    width: 100%;
    padding: 10px;
    background: #e4e4e4;
    border-radius: 5px;
    margin: 20px;
    margin-top: 400px;
  }
  .main {


    display: flex;
    flex-direction: column-reverse;
  }
  .result {
    margin-left: -350px;
    display: block;
    transform: rotate(-90deg);
    margin-top: 400px;
    border-radius: 10px;

    background: #b0b0b0;

    display: flex;

  }
  .backblaze {

  }
  .line {
    height: 50px;
    margin-top: -20px;

  }
  .name {
    width: 50px;
    height: 30px;
    transform: rotate(90deg);
  }
  .img {
    width: 100%;
    height: 30px;
  }
  .buttons {

    color: #000;
    transform: rotate(90deg);
    margin-left: -90px;
    margin-top: -5px;
    border-radius: 5px;
  }
  .btn {
    color: #000;

    text-align: center;
    padding: 5px;
    font-size: 14px;
    height: 20px;
    margin-left: -0px;
    border: 1px solid #000;
    border-radius: 5px;
  }
  .dinamicResultbackblaze {
    height: 40px;
    background: rgb(213, 213, 214);
    border-radius: 3px;
    max-width: 800px;
    margin-left: -100px;
    margin-top: 15px;
  }
  .dinamicResultbunny {
    height: 40px;
    background: rgb(213, 213, 214);
    border-radius: 3px;
    max-width: 800px;
    margin-left: -100px;
    margin-top: 15px;
  }
  .dinamicResultscaleway {
    height: 40px;
    background: rgb(213, 213, 214);
    border-radius: 3px;
    max-width: 800px;
    margin-left: -100px;
    margin-top: 15px;
  }
  .dinamicResultvultr {
    height: 40px;
    background: rgb(213, 213, 214);
    border-radius: 3px;
    max-width: 800px;
    margin-left: -100px;
    margin-top: 15px;
  }
  .backblaze {
    margin-left: 40px;

    margin-top: 30px;
    display: flex;
  }
  .bunny {
    margin-left: 40px;
    margin-top: 30px;
    display: flex;
  }
  .scaleway {
    margin-left: 40px;
    margin-top: 30px;

    display: flex;
  }
  .vultr {
    margin-left: 40px;
    margin-top: 30px;
    display: flex;
  }
  .sum {
    min-width: 40px;
    height: 20px;
    background: #37ff00;
    font-size: 16px;
    padding: 3px;
    border-radius: 3px;
    margin: 25px 0 0 -10px;
    transform: rotate(90deg);
  }
  .activeBtn {
    color: #000000;
    background: #72e407;
  }
  .slider {

    width: 1000px;
  }
  .green {
  background: #4dff00;
}
.red {
  background: rgb(255, 0, 0);
}

}
</style>
