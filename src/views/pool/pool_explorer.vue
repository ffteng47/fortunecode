<template>
  <el-container>
    <el-main>
      <el-row style="margin-bottom:10px;">
        <el-col :span="8">
          <div class="grid-content">
            <div class="grid-content">
              <span style="color:#919CAE;font-size:12px;font-weight:bold;">V0.1.0 MARKETDATA LIVE STREAM</span>
            </div>
            <div class="grid-content">
              <span
                style="color:#16BDDB;font-size:16px;font-weight:bold;"
              >Pool Explorer</span>
            </div>
          </div>
        </el-col>
        <el-col :span="8">
          <div class="grid-content">&nbsp;</div>
        </el-col>
        <el-col :span="8">
         
            <div style = "padding:10px; padding-top:15px;height:65px; box-shadow: 0 2px 4px rgba(0, 0, 0, .12), 0 0 6px rgba(0, 0, 0, .04)">
              <el-form :inline="true">
                <el-form-item>
                  <el-select v-model="value" placeholder="请选择">
                    <el-option
                      v-for="item in options"
                      :key="item.value"
                      :label="item.label"
                      :value="item.value"
                    ></el-option>
                  </el-select>
                </el-form-item>
                <el-form-item>
                  <el-input style="width:300px;" placeholder="Filter by token"></el-input>
                </el-form-item>
              </el-form>
            </div>
          
        </el-col>
      </el-row>

      <el-row>
        <el-col :span="24">
          <el-table :data="tableData" height="550" border style="width: 100%"
            :row-style="{height:32+'px'}"
            :cell-style="{padding:0+'px'}" @row-click="clickData">
            <el-table-column prop="exchange" label="exchange" ></el-table-column>
            <el-table-column prop="instrumentID" label="InstrumentID" ></el-table-column>
            <el-table-column prop="tradingDay" label="TradingDay" ></el-table-column>
            <el-table-column prop="tokenPrice" label="Token Price USD(ETH)" />
            <el-table-column prop="totalValue" label="Total Value" />
            <el-table-column prop="tokenAmount" label="Token Amount" />
            <el-table-column prop="ethAmount" label="ETH Amount" />
            <el-table-column prop="poolVariation" label="Pool Varation" />
            <el-table-column prop="poolRemaining" label="Pool Remaining" />
            <el-table-column prop="Option" label="Option" >
                <el-button @click="showDetail()">view detail</el-button>
                <!--<router-link to="/pair">
                    
                </router-link>-->
                
            </el-table-column>
          </el-table>
        </el-col>
      </el-row>
    </el-main>
  </el-container>
</template>

<style>
  .el-row {
    margin-bottom: 0px;
    &:last-child {
      margin-bottom: 0;
    }
  }
  .el-col {
    border-radius: 4px;
  }
  .grid-content {
    border-radius: 4px;
    min-height: 25px;
  }
  .row-bg {
    padding: 5px 0;
    background-color: #ffffff;
  }
</style>

<script>
export default {
    methods:{
        showDetail(params) {
            console.log(params); 
            console.log(this.tableData[8]);  
            this.$router.push({path:'/pair',query:{userid:123456}});   
        },
        clickData(row, event, column) {   
　　　　     console.log(row,  event,  column)
            console.log(this.tableData[0]={
                exchange: "shfe",
                instrumentID: "ni2010",
                actions: "helo",
                type: "ADD",
                tokenPrice: "$2.7717257"})
        } 
    },
  data() {
    return {
      options: [
        {
          value: "0",
          label: "View All",
        },
        {
          value: "1",
          label: "Removes",
        },
        {
          value: "2",
          label: "Adds",
        },
        {
          value: "3",
          label: "New",
        },
      ],
      value: "",
      tableData: [
        {
          exchange: "AMPL",
          instrumentID: "3 m 10 s",
          tradingDay: "20201020",
          type: "ADD",
          tokenPrice: "$2.7717257",
          totalValue: "$1,619.05",
          tokenAmount: "30,352.27456 AMPL",
          ethAmount: "59.88478 ETH",
          poolVariation: "0.11%",
          poolRemaining: "55,513.52073 ETH",
          pairCreated: "+ 110 days",
        },
        {
          token: "COMP",
          time: "3 m 10 s",
          actions: "",
          type: "REMOVE",
          tokenPrice: "$2.7717257",
          totalValue: "$1,619.05",
          tokenAmount: "30,352.27456 COMP",
          ethAmount: "59.88478 ETH",
          poolVariation: "0.11%",
          poolRemaining: "55,513.52073 ETH",
          pairCreated: "+ 110 days",
        },
        {
          token: "SUSHI",
          time: "3 m 10 s",
          actions: "",
          type: "ADD",
          tokenPrice: "$2.7717257",
          totalValue: "$1,619.05",
          tokenAmount: "30,352.27456 SUSHI",
          ethAmount: "59.88478 ETH",
          poolVariation: "0.11%",
          poolRemaining: "55,513.52073 ETH",
          pairCreated: "+ 110 days",
        },
        {
          token: "AMPL",
          time: "3 m 10 s",
          actions: "",
          type: "ADD",
          tokenPrice: "$2.7717257",
          totalValue: "$1,619.05",
          tokenAmount: "30,352.27456 AMPL",
          ethAmount: "59.88478 ETH",
          poolVariation: "0.11%",
          poolRemaining: "55,513.52073 ETH",
          pairCreated: "+ 110 days",
        },
        {
          token: "COMP",
          time: "3 m 10 s",
          actions: "",
          type: "REMOVE",
          tokenPrice: "$2.7717257",
          totalValue: "$1,619.05",
          tokenAmount: "30,352.27456 COMP",
          ethAmount: "59.88478 ETH",
          poolVariation: "0.11%",
          poolRemaining: "55,513.52073 ETH",
          pairCreated: "+ 110 days",
        },
        {
          token: "SUSHI",
          time: "3 m 10 s",
          actions: "",
          type: "ADD",
          tokenPrice: "$2.7717257",
          totalValue: "$1,619.05",
          tokenAmount: "30,352.27456 SUSHI",
          ethAmount: "59.88478 ETH",
          poolVariation: "0.11%",
          poolRemaining: "55,513.52073 ETH",
          pairCreated: "+ 110 days",
        },
        {
          token: "AMPL",
          time: "3 m 10 s",
          actions: "",
          type: "ADD",
          tokenPrice: "$2.7717257",
          totalValue: "$1,619.05",
          tokenAmount: "30,352.27456 AMPL",
          ethAmount: "59.88478 ETH",
          poolVariation: "0.11%",
          poolRemaining: "55,513.52073 ETH",
          pairCreated: "+ 110 days",
        },
        {
          token: "COMP",
          time: "3 m 10 s",
          actions: "",
          type: "REMOVE",
          tokenPrice: "$2.7717257",
          totalValue: "$1,619.05",
          tokenAmount: "30,352.27456 COMP",
          ethAmount: "59.88478 ETH",
          poolVariation: "0.11%",
          poolRemaining: "55,513.52073 ETH",
          pairCreated: "+ 110 days",
        },
        {
          token: "SUSHI",
          time: "3 m 10 s",
          actions: "",
          type: "ADD",
          tokenPrice: "$2.7717257",
          totalValue: "$1,619.05",
          tokenAmount: "30,352.27456 SUSHI",
          ethAmount: "59.88478 ETH",
          poolVariation: "0.11%",
          poolRemaining: "55,513.52073 ETH",
          pairCreated: "+ 110 days",
        },
      ],
    };
  },
};
</script>
