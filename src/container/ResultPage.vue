<template>
  <main-wrapper>
    <el-card
      class="result-card"
      shadow="always"
    >
      <div class="charts-container">
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
      let upperMappedData, lowerMappedData;
      
      if (this.chartType === 'mbt') {
        const upperCV = Number(parseInt(this.upperValue) / 2).toFixed(1);
        const lowerCV = Number(parseInt(this.lowerValue) / 2).toFixed(1);
        upperMappedData = mbtMapping.upper[upperCV.toString()];
        lowerMappedData = mbtMapping.lower[lowerCV.toString()];
      } else if (this.chartType === 'sap') {
        upperMappedData = sapMapping.upper[parseInt(this.upperValue)];
        lowerMappedData = sapMapping.lower[parseInt(this.lowerValue)];
      }

      const upperTableData = {};
      const lowerTableData = {};
      headerData.forEach((val, index) => {
        upperTableData[index] = upperMappedData[index];
        lowerTableData[index] = lowerMappedData[index];
      });
      duplicatedHeaderData.forEach((val, index) => {

        upperTableData[index] = upperMappedData[upperMappedData.length - index - 2]
        lowerTableData[index] = lowerMappedData[lowerMappedData.length - index - 2];
      });
      this.upperTableData[0] = headerData.concat(duplicatedHeaderData);
      this.upperTableData[1] = Object.values(upperTableData).reverse().concat(Object.values(upperTableData));
      this.lowerTableData[0] = Object.values(lowerTableData).reverse().concat(Object.values(lowerTableData));
      this.lowerTableData[1] = headerData.concat(duplicatedHeaderData);
    },
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
  justify-content: center;
  align-items: center;
}
.charts-wrapper {
  height: 90%;
  width: 100%;
  border-radius: 20px;
  padding: 10px 0;
  box-shadow: 0 10px 20px rgba(0,0,0,0.19), 0 6px 6px rgba(0,0,0,0.23);
}
.upper, .lower {
  height: 50%;
  margin: 5px;
  display: flex;
  flex-direction: column;
}
.upper > span, .lower > span {
  text-align: left;
  margin-bottom: 10px;
}
.upper-container, .lower-container {
  flex-grow: 1;
  display: flex;
  justify-content: center;
  align-items: center;
}
.result-table {
  padding-top: 20px;
  width: 100%;
}
.el-table__header, .el-table__body {
  width: 100% !important;
}
.el-table__body > tbody > tr > td {
  border-bottom: 2px solid black;
}
.el-table__body > tbody > tr ~ tr > td {
  border-bottom: none;
}
.result-table.upper > .el-table__body-wrapper > .el-table__body > tbody > tr:nth-child(1) > td:nth-child(5) {
  border-right: 2px solid black;
}
.result-table.lower > .el-table__body-wrapper > .el-table__body > tbody > tr:nth-child(2) > td:nth-child(5) {
  border-right: 2px solid black;
}
</style>