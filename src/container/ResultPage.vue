<template>
  <main-wrapper>
    <el-card
      class="result-card"
      shadow="always"
    >
      <div class="charts-container">
        <div class="back-button" @click="goToHome()">Home</div>
        <div class="charts-wrapper">
          <div class="upper">
            <span>UPPER</span>
            <div class="upper-container">
              <el-table
                class="result-table upper"
                :data="upperTableData"
                :show-header="false">
                <el-table-column
                  v-for="(value, index) in Object.keys(upperTableData[0])"
                  :prop="value"
                  :label="value"
                  :key="index"
                  >
                </el-table-column>
              </el-table>
            </div>
          </div>
          <div class="lower red">
            <div>
              <svg id="" preserveAspectRatio="xMidYMax meet" class="svg-separator sep1" viewBox="0 0 1600 100" style="" data-height="100">
                <path class="" style="opacity: 1;fill: #bc4565;" d="M1040,56c0.5,0,1,0,1.6,0c-16.6-8.9-36.4-15.7-66.4-15.7c-56,0-76.8,23.7-106.9,41C881.1,89.3,895.6,96,920,96
                C979.5,96,980,56,1040,56z"></path>
                <path class="" style="opacity: 1;fill: #bc4565;" d="M1699.8,96l0,10H1946l-0.3-6.9c0,0,0,0-88,0s-88.6-58.8-176.5-58.8c-51.4,0-73,20.1-99.6,36.8
                c14.5,9.6,29.6,18.9,58.4,18.9C1699.8,96,1699.8,96,1699.8,96z"></path>
                <path class="" style="opacity: 1;fill: #bc4565;" d="M1400,96c19.5,0,32.7-4.3,43.7-10c-35.2-17.3-54.1-45.7-115.5-45.7c-32.3,0-52.8,7.9-70.2,17.8
                c6.4-1.3,13.6-2.1,22-2.1C1340.1,56,1340.3,96,1400,96z"></path>
                <path class="" style="opacity: 1;fill: #bc4565;" d="M320,56c6.6,0,12.4,0.5,17.7,1.3c-17-9.6-37.3-17-68.5-17c-60.4,0-79.5,27.8-114,45.2
                c11.2,6,24.6,10.5,44.8,10.5C260,96,259.9,56,320,56z"></path>
                <path class="" style="opacity: 1;fill: #bc4565;" d="M680,96c23.7,0,38.1-6.3,50.5-13.9C699.6,64.8,679,40.3,622.2,40.3c-30,0-49.8,6.8-66.3,15.8
                c1.3,0,2.7-0.1,4.1-0.1C619.7,56,620.2,96,680,96z"></path>
                <path class="" style="opacity: 1;fill: #bc4565;" d="M-40,95.6c28.3,0,43.3-8.7,57.4-18C-9.6,60.8-31,40.2-83.2,40.2c-14.3,0-26.3,1.6-36.8,4.2V106h60V96L-40,95.6
                z"></path>
                <path class="" style="opacity: 1;fill: #af3f5d;" d="M504,73.4c-2.6-0.8-5.7-1.4-9.6-1.4c-19.4,0-19.6,13-39,13c-19.4,0-19.5-13-39-13c-14,0-18,6.7-26.3,10.4
                C402.4,89.9,416.7,96,440,96C472.5,96,487.5,84.2,504,73.4z"></path>
                <path class="" style="opacity: 1;fill: #af3f5d;" d="M1205.4,85c-0.2,0-0.4,0-0.6,0c-19.5,0-19.5-13-39-13s-19.4,12.9-39,12.9c0,0-5.9,0-12.3,0.1
                c11.4,6.3,24.9,11,45.5,11C1180.6,96,1194.1,91.2,1205.4,85z"></path>
                <path class="" style="opacity: 1;fill: #af3f5d;" d="M1447.4,83.9c-2.4,0.7-5.2,1.1-8.6,1.1c-19.3,0-19.6-13-39-13s-19.6,13-39,13c-3,0-5.5-0.3-7.7-0.8
                c11.6,6.6,25.4,11.8,46.9,11.8C1421.8,96,1435.7,90.7,1447.4,83.9z"></path>
                <path class="" style="opacity: 1;fill: #af3f5d;" d="M985.8,72c-17.6,0.8-18.3,13-37,13c-19.4,0-19.5-13-39-13c-18.2,0-19.6,11.4-35.5,12.8
                c11.4,6.3,25,11.2,45.7,11.2C953.7,96,968.5,83.2,985.8,72z"></path>
                <path class="" style="opacity: 1;fill: #af3f5d;" d="M743.8,73.5c-10.3,3.4-13.6,11.5-29,11.5c-19.4,0-19.5-13-39-13s-19.5,13-39,13c-0.9,0-1.7,0-2.5-0.1
                c11.4,6.3,25,11.1,45.7,11.1C712.4,96,727.3,84.2,743.8,73.5z"></path>
                <path class="" style="opacity: 1;fill: #af3f5d;" d="M265.5,72.3c-1.5-0.2-3.2-0.3-5.1-0.3c-19.4,0-19.6,13-39,13c-19.4,0-19.6-13-39-13
                c-15.9,0-18.9,8.7-30.1,11.9C164.1,90.6,178,96,200,96C233.7,96,248.4,83.4,265.5,72.3z"></path>
                <path class="" style="opacity: 1;fill: #af3f5d;" d="M1692.3,96V85c0,0,0,0-19.5,0s-19.6-13-39-13s-19.6,13-39,13c-0.1,0-0.2,0-0.4,0c11.4,6.2,24.9,11,45.6,11
                C1669.9,96,1684.8,96,1692.3,96z"></path>
                <path class="" style="opacity: 1;fill: #af3f5d;" d="M25.5,72C6,72,6.1,84.9-13.5,84.9L-20,85v8.9C0.7,90.1,12.6,80.6,25.9,72C25.8,72,25.7,72,25.5,72z"></path>
                <path class="" style="fill: rgb(210, 77, 87);" d="M-40,95.6C20.3,95.6,20.1,56,80,56s60,40,120,40s59.9-40,120-40s60.3,40,120,40s60.3-40,120-40
                s60.2,40,120,40s60.1-40,120-40s60.5,40,120,40s60-40,120-40s60.4,40,120,40s59.9-40,120-40s60.3,40,120,40s60.2-40,120-40
                s60.2,40,120,40s59.8,0,59.8,0l0.2,143H-60V96L-40,95.6z"></path>
              </svg>
              <div class="lower">
              <span>LOWER</span>
              <div class="lower-container">
                <el-table
                  class="result-table lower"
                  :data="lowerTableData"
                  :show-header="false">
                  <el-table-column
                    v-for="value in Object.keys(lowerTableData[0])"
                    :prop="value"
                    :label="value"
                    :key="value"
                    >
                  </el-table-column>
                </el-table>
              </div>
            </div>
            </div>
          </div>
        </div>
      </div>
    </el-card>
  </main-wrapper>
</template>
<script>
// @ is an alias to /src
import MainWrapper from '@/components/MainWrapper/index.vue';

const mbtMapping = {
  upper: {
    '6.0': ['5.0', '5.5', '6.0', '5.5', '6.0', '+1.0 mm'],
    '5.5': ['4.5', '5.0', '5.5', '5.0', '5.5', '+0.5 mm'],
    '5.0': ['4.0', '4.5', '5.0', '4.5', '5.0', 'Average'],
    '4.5': ['3.5', '4.0', '4.5', '4.0', '4.5', '-0.5 mm'],
    '4.0': ['3.0', '3.5', '4.0', '3.5', '4.0', '-1.0 mm'],
  },
  lower: {
    '5.5': ['4.5', '5.0', '5.5', '5.0', '5.0', '+1.0 mm'],
    '5.0': ['4.0', '4.5', '5.0', '4.5', '4.5', '+0.5 mm'],
    '4.5': ['3.5', '4.0', '4.5', '4.0', '4.0', 'Average'],
    '4.0': ['3.0', '3.5', '4.0', '3.5', '3.5', '-0.5 mm'],
    '3.5': ['2.5', '3.0', '3.5', '3.0', '3.0', '-1.0 mm'],
  },
};

const sapMapping = {
  upper: {
    '12': ['5.0', '5.5', '6.0', '6.0', '7.0'],
    '11': ['4.5', '5.0', '5.5', '5.5', '6.5'],
    '10': ['4.0', '4.5', '5.0', '5.0', '5.5'],
    '9': ['3.5', '4.0', '4.5', '4.5', '5.0'],
  },
  lower: {
    '11': ['5.5', '6.0', '6.0', '5.0', '5.0'],
    '10': ['5.0', '5.5', '5.5', '5.0', '5.0'],
    '9': ['4.5', '5.0', '5.0', '4.5', '4.5'],
    '8': ['4.0', '4.5', '4.5', '4.0', '4.0'],
  }
}

export default {
  name: 'ResultPage',
  components: {
    MainWrapper,
  },
  created() {
    this.createAxes();
  },
  data() {
    return {
      upperTableData: [],
      lowerTableData: []
    }
  },
  methods: {
    createAxes() {
      this.upperValue = this.$route.query.upperValue;
      this.lowerValue = this.$route.query.lowerValue;
      this.chartType = this.$route.query.chartType;
      const headerData = ['5', '4', '3', '2', '1'];
      const duplicatedHeaderData = ['-1', '-2', '-3', '-4', '-5'];
      let upperMappedData, lowerMappedData, cutValue;
      
      if (this.chartType === 'mbt') {
        const upperCV = Number(parseInt(this.upperValue) / 2).toFixed(1);
        const lowerCV = Number(parseInt(this.lowerValue) / 2).toFixed(1);
        upperMappedData = mbtMapping.upper[upperCV.toString()];
        lowerMappedData = mbtMapping.lower[lowerCV.toString()];
        cutValue = 2
      } else if (this.chartType === 'sap') {
        upperMappedData = sapMapping.upper[parseInt(this.upperValue)];
        lowerMappedData = sapMapping.lower[parseInt(this.lowerValue)];
        cutValue = 1;
      }

      const upperTableData = {};
      const lowerTableData = {};
      headerData.forEach((val, index) => {
        upperTableData[index] = upperMappedData[index];
        lowerTableData[index] = lowerMappedData[index];
      });
      duplicatedHeaderData.forEach((val, index) => {
        upperTableData[index] = upperMappedData[upperMappedData.length - index - cutValue];
        lowerTableData[index] = lowerMappedData[lowerMappedData.length - index - cutValue];
      });
      this.upperTableData[0] = headerData.concat(duplicatedHeaderData.map(val => val.slice(1)));
      this.upperTableData[1] = Object.values(upperTableData).reverse().concat(Object.values(upperTableData));
      this.lowerTableData[0] = Object.values(lowerTableData).reverse().concat(Object.values(lowerTableData));
      this.lowerTableData[1] = headerData.concat(duplicatedHeaderData.map(val => val.slice(1)));
    },
    goToHome() {
      this.$router.push({
        path: '/',
        query: {}
      });
    }
  }
}
</script>
<style>

.result-card {
  height: 100%;
}
.result-card > .el-card__body {
  height: 100%;
}
.charts-container {
  height: 100%;
  width: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.back-button {
  height: 50px;
  width: 150px;
  border: 1px solid black;
  border-radius: 10px;
  background-color: darkslategrey;
  color: white;
  padding: 10px;
  box-sizing: border-box;
  font-size: 24px;
  font-weight: 600;
  cursor: pointer;
}
.charts-wrapper {
  height: 100%;
  width: 100%;
  border-radius: 20px;
  box-shadow: 0 10px 20px rgba(0,0,0,0.19), 0 6px 6px rgba(0,0,0,0.23);
  display: flex;
  flex-direction: column;
  margin-top: 5px;
}
.upper, .lower {
  height: 50%;
  display: flex;
  flex-direction: column;
  position:relative;
}
.upper > span, .lower > span {
  text-align: left;
  font-size: 24px;
  font-weight: 600;
  color: #d24d57;
  padding: 10px 10px;
}
.lower > span {
  color: white;
}
.upper-container, .lower-container {
  flex-grow: 1;
}

/* -- SVG CSS -- */

.svg-separator{
  display: block;
  background: 0 0;
  position: absolute;
  left: 0;
  right: 0;
  top: 0;
  z-index: 9;
  -webkit-transform: translateY(-100%) translateY(2px);
  transform: translateY(-100%) translateY(2px);
  width: 100%;
}
.sep1{
  transform: translateY(-100%) translateY(2px) scale(1,1);
  transform-origin: top;
}
.red{background-color:#d24d57;}

.result-table {
  padding-top: 20px;
  width: 100%;
  font-size: 24px;
}
.result-table.upper {
  color: #d24d57;
}
.result-table.lower {
  color: white;
}
.el-table__header, .el-table__body {
  width: 100% !important;
}
.result-table.upper > .el-table__body-wrapper > .el-table__body > tbody > tr > td {
  border-bottom: 2px solid #d24d57;
}
.result-table.upper > .el-table__body-wrapper > .el-table__body > tbody > tr ~ tr > td {
  border-bottom: none;
}
.result-table.lower > .el-table__body-wrapper > .el-table__body > tbody > tr > td {
  border-bottom: 2px solid white;
}
.result-table.lower > .el-table__body-wrapper > .el-table__body > tbody > tr ~ tr > td {
  border-bottom: none;
}
.result-table.upper > .el-table__body-wrapper > .el-table__body > tbody > tr:nth-child(1) > td:nth-child(5) {
  border-right: 2px solid #d24d57;
}
.result-table.lower > .el-table__body-wrapper > .el-table__body > tbody > tr:nth-child(2) > td:nth-child(5) {
  border-right: 2px solid white;
}
</style>