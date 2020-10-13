<template>
  <el-container>
    <el-main>
      <el-row style="margin-bottom:10px;">
        <el-col :span="8">
          <div class="grid-content">
            <span style="color:#919CAE;font-size:12px;font-weight:bold;">V0.1.0 MARKETDATA LIVE STREAM</span>
          </div>
          <div class="grid-content">
            <span
              style="color:#16BDDB;font-size:16px;font-weight:bold;"
            ></span>
          </div>
        </el-col>
        <el-col :span="8">
          <div class="grid-content">&nbsp;</div>
        </el-col>
        <el-col :span="8">
          <div
            style="padding:10px; padding-top:15px;height:65px; box-shadow: 0 2px 4px rgba(0, 0, 0, .12), 0 0 6px rgba(0, 0, 0, .04)"
          >
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
                <el-input style="width:300px;" placeholder="NI2010"></el-input>
              </el-form-item>
            </el-form>
          </div>
        </el-col>
      </el-row>
        <el-row >
            <el-col :span="4" style="color:#16BDDB;font-size:16px;font-weight:bold;">EXCHANGE:</el-col>
            <el-col :span="8">{{this.$route.query.exchangeid}}</el-col>
        </el-row>
        <el-row >
            <el-col :span="4" style="color:#16BDDB;font-size:16px;font-weight:bold;">INSTRUMENT:</el-col>
            <el-col :span="8">{{this.$route.query.instrumentID}}</el-col>
        </el-row>
      <el-row>
        <el-col :span="8">
          <!--<el-row>
            <el-col :span="10">
              <el-row>
                <el-col :span="24">
                  <el-row>
                    <span style="color:#16BDDB;font-size:12px;">
                      GET FULL ACCESS
                      <br />HOLD 5000 DEXT
                      <br />NO DELAY, MORE INFO..
                    </span>
                  </el-row>
                  <el-row>
                    <el-button type="success" size="small">BUY DEXT</el-button>
                  </el-row>
                </el-col>
              </el-row>
            </el-col>
            <el-col :span="14" style="color:##5F656D;">
              <el-row style="height:40px;">
                <el-col :span="24" style="text-align:right;">
                  <el-button type="danger" size="small">Trade</el-button>
                </el-col>
              </el-row>
              <el-row>
                <el-col :span="24" style="text-align:right;line-height:30px;">$0.05882415</el-col>
              </el-row>
              <el-row>
                <el-col :span="24" style="text-align:right;line-height:30px;">0.00015249 ETH</el-col>
              </el-row>
              <el-row style="font-size:11px;">
                <el-col :span="12">Total liquidity:</el-col>
                <el-col :span="12" style="text-align:right;line-height:30px;">$477,580.57</el-col>
              </el-row>
              <el-row style="font-size:11px;">
                <el-col :span="12">Daily volume:</el-col>
                <el-col :span="12" style="text-align:right;line-height:30px;">$223,375.47</el-col>
              </el-row>
              <el-row style="font-size:11px;">
                <el-col :span="12">Pooled ETH:</el-col>
                <el-col :span="12" style="text-align:right;line-height:30px;">621.38</el-col>
              </el-row>
              <el-row style="font-size:11px;">
                <el-col :span="12">Pooled DEXT:</el-col>
                <el-col :span="12" style="text-align:right;line-height:30px;">4,082,165.96</el-col>
              </el-row>
              <el-row style="font-size:11px;">
                <el-col :span="12">Total tx:</el-col>
                <el-col :span="12" style="text-align:right;line-height:30px;">34779</el-col>
              </el-row>
            </el-col>
          </el-row>-->
          <!--<el-row>
            <el-col :span="24">
              
              
              <el-row style="font-size:11px;">
                <el-col :span="18">
                    
                    <div style="width:100%;height:200px;font-size:12px;margin-top:50px;" ref="chartdiv1"></div>
                </el-col>
                <el-col :span="6" style="text-align:center;line-height:30px;padding-top:80px;">
                    <el-row style="font-size:11px;">
                        <el-col :span="24">DEXT Score</el-col>
                    </el-row>
                    <el-row style="font-size:11px;">
                        <el-col :span="24">
                            <span style="color:#17C671;font-size:52px;font-weight:bold;margin-top:20px;">97</span>
                        </el-col>
                    </el-row>
                </el-col>
              </el-row>
              
            </el-col>
          </el-row>-->
        </el-col>
        <el-col :span="24">
          <!-- 图表 -->
          <div class="hello" ref="chartdiv"></div>
        </el-col>
      </el-row>

      <el-row style="margin-top:30px;">
        <el-col :span="24">
          <!--<el-table
            :data="tableData"
            height="550"
            border
            style="width: 100%"
            :row-style="{height:32+'px'}"
            :cell-style="{padding:0+'px'}"
          >
            <el-table-column prop="date" label="Date" />
            <el-table-column prop="type" label="Type" />
            <el-table-column prop="usdPrice" label="Price(USD)" />
            <el-table-column prop="ethPrice" label="Price(ETH)" />
            <el-table-column prop="amountDext" label="AmountDEXT" />
            <el-table-column prop="totalEth" label="TotalEth" />
            <el-table-column prop="maker" label="Maker" />
          </el-table>-->
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
.hello {
  width: 100%;
  height: 500px;
}
</style>

<script>
import * as am4core from "@amcharts/amcharts4/core";
import * as am4charts from "@amcharts/amcharts4/charts";
import am4themes_animated from "@amcharts/amcharts4/themes/animated";

/* Chart code */
// Themes begin
am4core.useTheme(am4themes_animated);
// Themes end

/**
 * Set up external controls
 */

// Date format to be used in input fields
/**
let inputFieldFormat = "yyyy-MM-dd";

document.getElementById("b1m").addEventListener("click", function() {
  let max = dateAxis.groupMax["day1"];
  let date = new Date(max);
  am4core.time.add(date, "month", -1);
  zoomToDates(date);
});

document.getElementById("b3m").addEventListener("click", function() {
  let max = dateAxis.groupMax["day1"];
  let date = new Date(max);
  am4core.time.add(date, "month", -3);
  zoomToDates(date);
});

document.getElementById("b6m").addEventListener("click", function() {
  let max = dateAxis.groupMax["day1"];
  let date = new Date(max);
  am4core.time.add(date, "month", -6);
  zoomToDates(date);
});

document.getElementById("b1y").addEventListener("click", function() {
  let max = dateAxis.groupMax["day1"];
  let date = new Date(max);
  am4core.time.add(date, "year", -1);
  zoomToDates(date);
});

document.getElementById("bytd").addEventListener("click", function() {
  let max = dateAxis.groupMax["day1"];
  let date = new Date(max);
  am4core.time.round(date, "year", 1);
  zoomToDates(date);
});

document.getElementById("bmax").addEventListener("click", function() {
  let min = dateAxis.groupMin["day1"];
  let date = new Date(min);
  zoomToDates(date);
});

dateAxis.events.on("selectionextremeschanged", function() {
  updateFields();
});

dateAxis.events.on("extremeschanged", updateFields);

function updateFields() {
  let minZoomed = dateAxis.minZoomed + am4core.time.getDuration(dateAxis.mainBaseInterval.timeUnit, dateAxis.mainBaseInterval.count) * 0.5;
  document.getElementById("fromfield").value = chart.dateFormatter.format(minZoomed, inputFieldFormat);
  document.getElementById("tofield").value = chart.dateFormatter.format(new Date(dateAxis.maxZoomed), inputFieldFormat);
}

document.getElementById("fromfield").addEventListener("keyup", updateZoom);
document.getElementById("tofield").addEventListener("keyup", updateZoom);
 */

let zoomTimeout;
function updateZoom() {
  if (zoomTimeout) {
    clearTimeout(zoomTimeout);
  }
  zoomTimeout = setTimeout(function () {
    let start = document.getElementById("fromfield").value;
    let end = document.getElementById("tofield").value;
    if (
      start.length < inputFieldFormat.length ||
      end.length < inputFieldFormat.length
    ) {
      return;
    }
    let startDate = chart.dateFormatter.parse(start, inputFieldFormat);
    let endDate = chart.dateFormatter.parse(end, inputFieldFormat);

    if (startDate && endDate) {
      dateAxis.zoomToDates(startDate, endDate);
    }
  }, 500);
}

function zoomToDates(date) {
  let min = dateAxis.groupMin["day1"];
  let max = dateAxis.groupMax["day1"];
  dateAxis.keepSelection = true;
  //dateAxis.start = (date.getTime() - min)/(max - min);
  //dateAxis.end = 1;

  dateAxis.zoom({ start: (date.getTime() - min) / (max - min), end: 1 });
}
(function() {
    console.log("hello world");
});
export default {
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
      /*tableData: [
        {
          date: "2020-09-13 15:03:21",
          type: "buy",
          usdPrice: "$0.06125774",
          ethPrice: "0.00015845",
          amountDext: "5,000.00",
          totalEth: "0.79226254",
          maker: "0x953533d6d085c503f6ec78a66cb2f454d090faed",
        },
        {
          date: "2020-09-13 15:03:21",
          type: "buy",
          usdPrice: "$0.06125774",
          ethPrice: "0.00015845",
          amountDext: "5,000.00",
          totalEth: "0.79226254",
          maker: "0x953533d6d085c503f6ec78a66cb2f454d090faed",
        },
        {
          date: "2020-09-13 15:03:21",
          type: "buy",
          usdPrice: "$0.06125774",
          ethPrice: "0.00015845",
          amountDext: "5,000.00",
          totalEth: "0.79226254",
          maker: "0x953533d6d085c503f6ec78a66cb2f454d090faed",
        },
        {
          date: "2020-09-13 15:03:21",
          type: "buy",
          usdPrice: "$0.06125774",
          ethPrice: "0.00015845",
          amountDext: "5,000.00",
          totalEth: "0.79226254",
          maker: "0x953533d6d085c503f6ec78a66cb2f454d090faed",
        },
        {
          date: "2020-09-13 15:03:21",
          type: "buy",
          usdPrice: "$0.06125774",
          ethPrice: "0.00015845",
          amountDext: "5,000.00",
          totalEth: "0.79226254",
          maker: "0x953533d6d085c503f6ec78a66cb2f454d090faed",
        },
        {
          date: "2020-09-13 15:03:21",
          type: "buy",
          usdPrice: "$0.06125774",
          ethPrice: "0.00015845",
          amountDext: "5,000.00",
          totalEth: "0.79226254",
          maker: "0x953533d6d085c503f6ec78a66cb2f454d090faed",
        },
        {
          date: "2020-09-13 15:03:21",
          type: "buy",
          usdPrice: "$0.06125774",
          ethPrice: "0.00015845",
          amountDext: "5,000.00",
          totalEth: "0.79226254",
          maker: "0x953533d6d085c503f6ec78a66cb2f454d090faed",
        },
      ],*/
    };
  },

  mounted() {
    // Create chart
    // let chart = am4core.create("chartdiv", am4charts.XYChart);
    let chart = am4core.create(this.$refs.chartdiv, am4charts.XYChart);

    chart.padding(0, 15, 0, 15);
    console.log(this.$route.query)
    // Load data
    chart.dataSource.url = "http://localhost:3000/downloadfile?exchangeid=shfe"        
      //"https://www.amcharts.com/wp-content/uploads/assets/stock/MSFT.csv";
    chart.dataSource.parser = new am4core.CSVParser();
    chart.dataSource.parser.options.useColumnNames = true;
    chart.dataSource.parser.options.reverse = true;

    chart.inputFieldFormat="hh:mm:ss";
    chart.dateFormatter.dateFormat = "hh:mm:ss";

    console.log(chart.dataSource)
    // the following line makes value axes to be arranged vertically.
    chart.leftAxesContainer.layout = "vertical";

    // uncomment this line if you want to change order of axes
    //chart.bottomAxesContainer.reverseOrder = true;

    let dateAxis = chart.xAxes.push(new am4charts.DateAxis());
    dateAxis.dateFormatter = new am4core.DateFormatter();
    dateAxis.dateFormatter.dateFormat = "hh:mm:ss";
    dateAxis.renderer.grid.template.location = 0;
    dateAxis.renderer.ticks.template.length = 8;
    dateAxis.renderer.ticks.template.strokeOpacity = 0.1;
    dateAxis.renderer.grid.template.disabled = true;
    dateAxis.renderer.ticks.template.disabled = false;
    dateAxis.renderer.ticks.template.strokeOpacity = 0.2;
    dateAxis.renderer.minLabelPosition = 0.01;
    dateAxis.renderer.maxLabelPosition = 0.99;
    dateAxis.keepSelection = true;
    dateAxis.minHeight = 30;

    dateAxis.groupData = true;
    dateAxis.minZoomCount = 5;

    // these two lines makes the axis to be initially zoomed-in
    // dateAxis.start = 0.7;
    // dateAxis.keepSelection = true;

    let valueAxis = chart.yAxes.push(new am4charts.ValueAxis());
    valueAxis.tooltip.disabled = true;
    valueAxis.zIndex = 1;
    valueAxis.renderer.baseGrid.disabled = true;
    // height of axis
    valueAxis.height = am4core.percent(65);

    valueAxis.renderer.gridContainer.background.fill = am4core.color("#000000");
    valueAxis.renderer.gridContainer.background.fillOpacity = 0.05;
    valueAxis.renderer.inside = true;
    valueAxis.renderer.labels.template.verticalCenter = "bottom";
    valueAxis.renderer.labels.template.padding(2, 2, 2, 2);

    //valueAxis.renderer.maxLabelPosition = 0.95;
    valueAxis.renderer.fontSize = "0.8em";

    let series = chart.series.push(new am4charts.CandlestickSeries());
    series.dataFields.dateX = "Date";
    series.dataFields.openValueY = "Open";
    series.dataFields.valueY = "Close";
    series.dataFields.lowValueY = "Low";
    series.dataFields.highValueY = "High";
    series.clustered = false;
    series.tooltipText =
      "open: {openValueY.value}\nlow: {lowValueY.value}\nhigh: {highValueY.value}\nclose: {valueY.value}";
    series.name = "MSFT";
    series.defaultState.transitionDuration = 0;

    let valueAxis2 = chart.yAxes.push(new am4charts.ValueAxis());
    valueAxis2.tooltip.disabled = true;
    // height of axis
    valueAxis2.height = am4core.percent(35);
    valueAxis2.zIndex = 3;
    // this makes gap between panels
    valueAxis2.marginTop = 30;
    valueAxis2.renderer.baseGrid.disabled = true;
    valueAxis2.renderer.inside = true;
    valueAxis2.renderer.labels.template.verticalCenter = "bottom";
    valueAxis2.renderer.labels.template.padding(2, 2, 2, 2);
    //valueAxis.renderer.maxLabelPosition = 0.95;
    valueAxis2.renderer.fontSize = "0.8em";

    valueAxis2.renderer.gridContainer.background.fill = am4core.color(
      "#000000"
    );
    valueAxis2.renderer.gridContainer.background.fillOpacity = 0.05;

    let series2 = chart.series.push(new am4charts.ColumnSeries());
    series2.dataFields.dateX = "Date";
    series2.clustered = false;
    series2.dataFields.valueY = "Volume";
    series2.yAxis = valueAxis2;
    series2.tooltipText = "{valueY.value}";
    series2.name = "Series 2";
    // volume should be summed
    series2.groupFields.valueY = "sum";
    series2.defaultState.transitionDuration = 0;

    chart.cursor = new am4charts.XYCursor();

    let scrollbarX = new am4charts.XYChartScrollbar();

    let sbSeries = chart.series.push(new am4charts.LineSeries());
    sbSeries.dataFields.valueY = "Close";
    sbSeries.dataFields.dateX = "Date";
    scrollbarX.series.push(sbSeries);
    sbSeries.disabled = true;
    scrollbarX.marginBottom = 20;
    chart.scrollbarX = scrollbarX;
    scrollbarX.scrollbarChart.xAxes.getIndex(0).minHeight = undefined;

    /**

        let chart = am4core.create(this.$refs.chartdiv, am4charts.XYChart);

        chart.paddingRight = 20;

        let data = [];
        let visits = 10;
        for (let i = 1; i < 366; i++) {
        visits += Math.round((Math.random() < 0.5 ? 1 : -1) * Math.random() * 10);
        data.push({ date: new Date(2018, 0, i), name: "name" + i, value: visits });
        }

        chart.data = data;

        let dateAxis = chart.xAxes.push(new am4charts.DateAxis());
        dateAxis.renderer.grid.template.location = 0;

        let valueAxis = chart.yAxes.push(new am4charts.ValueAxis());
        valueAxis.tooltip.disabled = true;
        valueAxis.renderer.minWidth = 35;

        let series = chart.series.push(new am4charts.LineSeries());
        series.dataFields.dateX = "date";
        series.dataFields.valueY = "value";

        series.tooltipText = "{valueY.value}";
        chart.cursor = new am4charts.XYCursor();

        let scrollbarX = new am4charts.XYChartScrollbar();
        scrollbarX.series.push(series);
        chart.scrollbarX = scrollbarX;

        this.chart = chart;
      },
      beforeDestroy() {
        if (this.chart) {
            this.chart.dispose();
        }*/

    let chart1 = am4core.create(this.$refs.chartdiv1, am4charts.XYChart);
    chart1.padding(40, 40, 40, 40);

    let categoryAxis = chart1.yAxes.push(new am4charts.CategoryAxis());
    categoryAxis.renderer.grid.template.location = 0;
    categoryAxis.dataFields.category = "network";
    categoryAxis.renderer.minGridDistance = 1;
    categoryAxis.renderer.inversed = true;
    categoryAxis.renderer.grid.template.disabled = true;

    let valueAxis3 = chart1.xAxes.push(new am4charts.ValueAxis());
    valueAxis3.min = 0;

    let series3 = chart1.series.push(new am4charts.ColumnSeries());
    series3.dataFields.categoryY = "network";
    series3.dataFields.valueX = "MAU";
    series3.tooltipText = "{valueX.value}";
    series3.columns.template.strokeOpacity = 0;
    series3.columns.template.column.cornerRadiusBottomRight = 1;
    series3.columns.template.column.cornerRadiusTopRight = 1;

    let labelBullet = series3.bullets.push(new am4charts.LabelBullet());
    labelBullet.label.horizontalCenter = "left";
    labelBullet.label.dx = 10;
    labelBullet.label.text =
      "{values.valueX.workingValue.formatNumber('#.0as')}";
    labelBullet.locationX = 1;

    series.columns.template.adapter.add("fill", function (fill, target) {
      return chart.colors.getIndex(target.dataItem.index);
    });

    categoryAxis.sortBySeries = series3;
    chart1.data = [
      {
        network: "Information",
        MAU: 98,
      },
      {
        network: "Transactions",
        MAU: 80,
      },
      {
        network: "Holders",
        MAU: 92,
      },
      {
        network: "Creation",
        MAU: 92,
      },
      {
        network: "Pool",
        MAU: 93,
      },
    ];
  },
};
</script>
