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
            <el-col :span="8">SHFE</el-col>
        </el-row>
        <el-row >
            <el-col :span="4" style="color:#16BDDB;font-size:16px;font-weight:bold;">INSTRUMENT:</el-col>
            <el-col :span="8">NI2010</el-col>
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
am4core.ready(function() {

// Themes begin
am4core.useTheme(am4themes_animated);
// Themes end

// Create chart instance
var chart = am4core.create("chartdiv", am4charts.XYChart);

// Add data
chart.data = generateChartData();

// Create axes
var dateAxis = chart.xAxes.push(new am4charts.DateAxis());
dateAxis.renderer.minGridDistance = 50;

var valueAxis = chart.yAxes.push(new am4charts.ValueAxis());

// Create series
var series = chart.series.push(new am4charts.LineSeries());
series.dataFields.valueY = "visits";
series.dataFields.dateX = "date";
series.strokeWidth = 2;
series.minBulletDistance = 10;
series.tooltipText = "{valueY}";
series.tooltip.pointerOrientation = "vertical";
series.tooltip.background.cornerRadius = 20;
series.tooltip.background.fillOpacity = 0.5;
series.tooltip.label.padding(12,12,12,12)

// Add scrollbar
chart.scrollbarX = new am4charts.XYChartScrollbar();
chart.scrollbarX.series.push(series);

// Add cursor
chart.cursor = new am4charts.XYCursor();
chart.cursor.xAxis = dateAxis;
chart.cursor.snapToSeries = series;

function generateChartData() {
    var chartData = [];
    var firstDate = new Date();
    firstDate.setDate(firstDate.getDate() - 1000);
    var visits = 1200;
    for (var i = 0; i < 500; i++) {
        // we create date objects here. In your data, you can have date strings
        // and then set format of your dates using chart.dataDateFormat property,
        // however when possible, use date objects, as this will speed up chart rendering.
        var newDate = new Date(firstDate);
        newDate.setDate(newDate.getDate() + i);
        
        visits += Math.round((Math.random()<0.5?1:-1)*Math.random()*10);

        chartData.push({
            date: newDate,
            visits: visits
        });
    }
    return chartData;
}

}); // end am4core.ready()
</script>
