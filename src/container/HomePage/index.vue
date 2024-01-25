<template>
    <main-wrapper>
      <div class="container-top">
        <el-card
          class="card-style"
          shadow="always"
          header="OrthoEase"
          >
          BONDING MADE EASY
        </el-card>
      </div>
      <div class="container-middle">
        <el-card
          class="card-style card-input"
          shadow="always"
          header="Tooth Measurement (Canine)">
            <div class="hexagon">
              <el-input class="upper-text" type="text" placeholder="Upper" v-model="upperValue"></el-input>
              <el-input class="lower-text" type="text" placeholder="Lower" v-model="lowerValue"></el-input>
            </div>
          </el-card>
      </div>
      <div class="container-bottom">
        <el-card
          class="card-style card-button"
          shadow="always"
          header="MBT"
          @click.native="gotToResult('mbt')"
          >
          system
        </el-card>
        <el-card
          class="card-style card-button"
          shadow="always"
          header="SAP"
          @click.native="gotToResult('sap')"
          >
          prescription
        </el-card>
      </div>  
    </main-wrapper>
  </template>
  
  <script>
  // @ is an alias to /src
  import MainWrapper from '@/components/MainWrapper/index.vue';
  
  export default {
    name: 'HomeView',
    components: {
      MainWrapper,
    },
    data() {
      return {
        upperValue: '',
        lowerValue: '',
      }
    },
    methods: {
      gotToResult(chartType) {
        this.$router.push({
          path: '/result',
          query: {
            upperValue: this.upperValue,
            lowerValue: this.lowerValue,
            chartType,
          }
        });
      }
    }
  }
</script>
<style>
.container-top {
  height: 40%;
}
.container-middle, .container-bottom {
  height: 15%;
}
.container-top, .container-middle, .container-bottom {
    /* height: 50%; */
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
}
/* .container-top > .card-style {
  width: 70%;
} */
.card-style {
  width: 70%;
  /* border: 2px solid darkred; */
  border-radius: 20px;
  background-color: darkslategrey;
  padding: 10px 0;
  box-shadow: 0 10px 20px rgba(0,0,0,0.19), 0 6px 6px rgba(0,0,0,0.23);
}
.card-input {
  width: 50%;
}
.card-button {
  width: 30% !important;
  margin: 10px;
  cursor: pointer;
}
.card-style > .el-card__header {
  font-size: 40px;
  color: white;
  font-weight: 600;
}

.card-input > .el-card__header {
  font-size: 16px;
  color: white;
  font-weight: 600;
  margin-bottom: 10px;
}
.card-input > .el-card__body {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.card-style > .el-card__body {
  font-size: 20px;
  color: white;
}
.container-bottom > div:nth-child(1) {
  position: fixed;
  left: 0;
  margin-left: 5%;
}

.container-bottom > div:nth-child(2) {
  position: fixed;
  right: 0;
  margin-right: 5%;
}
.upper-text > input, .lower-text > input {
  border: none;
  background-color: orangered;
  text-align: center;
  color: white;
}
.upper-text > input {
  border-bottom: 2px solid black;
}

::placeholder {
  color: white;
  opacity: 1; /* Firefox */
}

::-ms-input-placeholder { /* Edge 12 -18 */
  color: white;
}

input[type=text]:focus {
  outline: none !important;
  border: none;
}
.upper-text > input:focus {
  border-bottom: 2px solid black;
}

.hexagon {
  background-color: orangered;
  width: 70%;
  -webkit-clip-path: polygon(25% 5%, 75% 5%, 100% 50%, 75% 95%, 25% 95%, 0% 50%);
  clip-path: polygon(25% 5%, 75% 5%, 100% 50%, 75% 95%, 25% 95%, 0% 50%);
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
</style>
  