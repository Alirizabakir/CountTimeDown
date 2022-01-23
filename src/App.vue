<template>
  <div
    class="font-oswald w-full min-w-full flex flex-col justify-center content-center mt-20"
  >
    <h1 class="text-5xl mr-auto ml-auto mb-10 font-bold bg-red-600 border-2 border-white text-white shadow-md p-2">New Years Eve</h1>
    <div class="test1 flex w-full content-center justify-center">
      <div class="flex content-center justify-center font-semibold">
        <div
          v-for="item in countDownData"
          :key="item"
          class="flex content-center justify-center"
        >
          <div class="flex flex-col">
            <div class="flex">
              <div class="text-7xl text-center">
                <transition-group
                  tag="div"
                  mode="ease-in-out"
                  enter-active-class="animate__animated animate__flipInY"
                  enter-leave-class="animate__animated animate__flipInY"
                  class="h-20 w-14 mx-1 text-white"
                >
                  <div class="box" v-if="item.num1 == 0">0</div>
                  <div class="box" v-if="item.num1 == 1">1</div>
                  <div class="box" v-if="item.num1 == 2">2</div>
                  <div class="box" v-if="item.num1 == 3">3</div>
                  <div class="box" v-if="item.num1 == 4">4</div>
                  <div class="box" v-if="item.num1 == 5">5</div>
                  <div class="box" v-if="item.num1 == 6">6</div>
                  <div class="box" v-if="item.num1 == 7">7</div>
                  <div class="box" v-if="item.num1 == 8">8</div>
                  <div class="box" v-if="item.num1 == 9">9</div>
                </transition-group>
              </div>
              <div class="text-7xl text-center flex flex-col">
                <transition-group
                  tag="div"
                  mode="ease-in-out"
                  enter-active-class="animate__animated animate__flipInY"
                  enter-leave-class="animate__animated animate__flipInY"
                  class="h-20 w-14 mx-1 text-white"
                >
                  <div class="box" v-if="item.num2 == 0">0</div>
                  <div class="box" v-if="item.num2 == 1">1</div>
                  <div class="box" v-if="item.num2 == 2">2</div>
                  <div class="box" v-if="item.num2 == 3">3</div>
                  <div class="box" v-if="item.num2 == 4">4</div>
                  <div class="box" v-if="item.num2 == 5">5</div>
                  <div class="box" v-if="item.num2 == 6">6</div>
                  <div class="box" v-if="item.num2 == 7">7</div>
                  <div class="box" v-if="item.num2 == 8">8</div>
                  <div class="box" v-if="item.num2 == 9">9</div>
                </transition-group>
              </div>
              <div
                v-if="item.num3 != null"
                class="test4 text-7xl text-center h-20"
              >
                <transition-group
                  tag="div"
                  mode="ease-in-out"
                  enter-active-class="animate__animated animate__flipInY"
                  enter-leave-class="animate__animated animate__flipInY"
                  class="h-20 w-14 mx-1 text-white"
                >
                  <div class="box" v-if="item.num3 == 0">0</div>
                  <div class="box" v-if="item.num3 == 1">1</div>
                  <div class="box" v-if="item.num3 == 2">2</div>
                  <div class="box" v-if="item.num3 == 3">3</div>
                  <div class="box" v-if="item.num3 == 4">4</div>
                  <div class="box" v-if="item.num3 == 5">5</div>
                  <div class="box" v-if="item.num3 == 6">6</div>
                  <div class="box" v-if="item.num3 == 7">7</div>
                  <div class="box" v-if="item.num3 == 8">8</div>
                  <div class="box" v-if="item.num3 == 9">9</div>
                </transition-group>
              </div>
            </div>
            <div class="text-center text-sm tracking-wide mt-2 font-normal text-white rounded-sm border border-white bg-red-600 shadow-md ">{{ item.name }}</div>
          </div>
          <div v-if="item.name != 'Seconds'" class="mx-4 text-7xl text-red-600">:</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      countDownData: [
        {
          name: "Days",
          num1: 0,
          num2: 0,
          num3: 0,
          active: true,
        },
        {
          name: "Hours",
          num1: 0,
          num2: 0,
          num3: null,
          active: true,
        },
        {
          name: "Minutes",
          num1: 0,
          num2: 0,
          num3: null,
          active: true,
        },
        {
          name: "Seconds",
          num1: 0,
          num2: 0,
          num3: null,
          active: false,
        },
      ],
      days: 0,
      hours: 0,
      seconds: 0,
      minutes: 0,
    };
  },
  methods: {
    displayData() {
      setInterval(() => {
        const newYears = "1 Jan 2023";
        const newYearsDate = new Date(newYears);
        const currentDate = new Date();

        const totalSeconds = (newYearsDate - currentDate) / 1000;
        const days = Math.floor(totalSeconds / 3600 / 24);
        const hours = Math.floor(totalSeconds / 3600) % 24;
        const minutes = Math.floor(totalSeconds / 60) % 60;
        const seconds = Math.floor(totalSeconds % 60);

        if (seconds.toString(10).length < 2) {
          this.countDownData[3].num1 = "0";
          this.countDownData[3].num2 = seconds.toString(10)[0];
        } else {
          this.countDownData[3].num1 = seconds.toString(10)[0];
          this.countDownData[3].num2 = seconds.toString(10)[1];
        }
        if (minutes.toString(10).length < 2) {
          this.countDownData[2].num1 = "0";
          this.countDownData[2].num2 = minutes.toString(10)[0];
        } else {
          this.countDownData[2].num1 = minutes.toString(10)[0];
          this.countDownData[2].num2 = minutes.toString(10)[1];
        }
        if (hours.toString(10).length < 2) {
          this.countDownData[1].num1 = "0";
          this.countDownData[1].num2 = hours.toString(10)[0];
        } else {
          this.countDownData[1].num1 = hours.toString(10)[0];
          this.countDownData[1].num2 = hours.toString(10)[1];
        }
        if (days.toString(10).length < 3) {
          this.countDownData[0].num1 = "0";
          this.countDownData[0].num2 = days.toString(10)[1];
          this.countDownData[0].num3 = days.toString(10)[2];
        } else {
          this.countDownData[0].num1 = days.toString(10)[0];
          this.countDownData[0].num2 = days.toString(10)[1];
          this.countDownData[0].num3 = days.toString(10)[2];
        }
      }, 1000);
    },
  },
  mounted() {
    this.displayData();
  },
};
</script>

<style lang="scss">
body {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  background-position: center center;
  background-size: cover;
  background-image: url(https://images.unsplash.com/photo-1603739421258-4aa79ad860df?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1209&q=80);


  #app {
    width: 100vw;

    span {
      width: 100%;
      max-height: 100%;
    }
  }
}
</style>
