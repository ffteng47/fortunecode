<template>
  <div :class="className" :style="{height:height,width:width}" >
    <!--<form action="http://localhost:3000/upload_file" method="post" target="stop" enctype="multipart/form-data">
        <input type="value" name='account'>
        <input type="file" name='user1'>
        <input type="submit" value="上传">
    </form>-->
    <!-- 阻止提交跳转页面 -->
    <iframe  name="stop" style="display:none;"></iframe> 
    <input type="file" name='user' id="uploadfiles" multiple="multiple"> 
    <input type="submit" value="upload file" v-on:click="tend">
  </div>
  
</template>

<script>
import echarts from 'echarts'
require('echarts/theme/macarons') // echarts theme
import resize from './mixins/resize'
import axios from 'axios'
import { stringify } from '@amcharts/amcharts4/.internal/core/utils/Utils'
import $ from 'jquery'

export default {
  mixins: [resize],
  props: {
    className: {
      type: String,
      default: 'chart'
    },
    width: {
      type: String,
      default: '100%'
    },
    height: {
      type: String,
      default: '350px'
    },
    autoResize: {
      type: Boolean,
      default: true
    },
    chartData: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      chart: null
    }
  },
  methods: {
      tend(){
          var coverstyle = '<style type="text/css" id="overstyle">'
			+'#overDiv{'
			 +'background-color: #000;'
			 +'width: 100%;'
			 +'height: 100%;'
			 +'left:0;'
			 +'top:0;/*FF IE7*/'
			 +'filter:alpha(opacity=40);/*IE*/'
			 +'opacity:0.4;/*FF*/'
			 +'z-index:9997;'
			 +'position:fixed!important;/*FF IE7*/'
			 +'position:absolute;/*IE6*/'
			 +'_top:       expression(eval(document.compatMode &&'
			 +'document.compatMode=="CSS1Compat") ?'
			 +'documentElement.scrollTop + (document.documentElement.clientHeight-this.offsetHeight)/2 :/*IE6*/'
			 +'document.body.scrollTop + (document.body.clientHeight - this.clientHeight)/2);/*IE5 IE5.5*/}'
			 +'</style>';
		var loadDiv = '<div id="load" style="width: 200px; padding: 5px 0; text-align: center; border: solid 1px #dddddd;'
			+'background-color: #f8f8f8; position: absolute; top: 50%; left: 50%; margin: -50px 0 0 -100px;'
			+'display: block; z-index: 9999;">'
			+'<img src="/weixin/images/ajax-loader1.gif" border="0" alt="loading..." />'
			+'<span style="display:block;">data loading...</span>'
			+'</div>'
            +'<div id="overDiv"></div>';
            $("body").append($(coverstyle));
		    $("body").append($(loadDiv));
            var f=document.getElementById("uploadfiles");
            console.log("文件数量="+f.files.length);
            for(var i = 0;i < f.files.length;i++){
                console.log(f.files[i]);
            }
            console.log("hello");
            var formData = new FormData() // 声明一个FormData对象
            //var formData = new window.FormData() // vue 中使用 window.FormData(),否则会报 'FormData isn't definded'
            formData.append('user', document.getElementById("uploadfiles").files[0]) // 'userfile' 这个名字要和后台获取文件的名字一样;
            var url="http://localhost:3000/upload_file"                                                                             //'userfile'是formData这个对象的键名
            console.log(document.getElementById("uploadfiles").files);
            var options = {  // 设置axios的参数
                    url: url,
                    data: formData,
                    method: 'post',
                    headers: { 
                    'Content-Type': 'multipart/form-data'
                    }
                };
            event.preventDefault();
            axios(options).then((res) => {
                console.log("发送成功:"+stringify(res));
                if(res.data.code == 0){
                    console.log("upload successfully:"+stringify(res));
                    alert("upload file(s) successfully!");  
                    this.stoploading(false);
                }else if(res.data.code == 1){
                     console.log("upload failed:"+stringify(res));
                    alert("upload file(s) failed!");  
                    this.stoploading(false);
                }
            }).catch((error)=>{
                    console.log("upload failed:"+stringify(error));
                    alert("upload file(s) failed!");  
                    this.stoploading(false);
            }) // 发送请求
      },
    trand(){
      var url="http://localhost:3000"
      axios.post(url+'/upload_file')
      .then(function (response) {
        console.log(response);
      })
      .catch(function (error) {
        console.log(error);
      });
    },
    //结束loading组件
	stoploading(quick){
		if(quick){
			$("#overDiv").detach();
			$("#load").detach();
		}else{
			$("#overDiv").fadeOut("slow").detach();
			$("#load").fadeOut("slow").detach();
		}
		$("style#overstyle").detach();
		
	}
    /*initChart() {
      this.chart = echarts.init(this.$el, 'macarons')
      this.setOptions(this.chartData)
    },
    setOptions({ expectedData, actualData } = {}) {
      this.chart.setOption({
        xAxis: {
          data: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun'],
          boundaryGap: false,
          axisTick: {
            show: false
          }
        },
        grid: {
          left: 10,
          right: 10,
          bottom: 20,
          top: 30,
          containLabel: true
        },
        tooltip: {
          trigger: 'axis',
          axisPointer: {
            type: 'cross'
          },
          padding: [5, 10]
        },
        yAxis: {
          axisTick: {
            show: false
          }
        },
        legend: {
          data: ['expected', 'actual']
        },
        series: [{
          name: 'expected', itemStyle: {
            normal: {
              color: '#FF005A',
              lineStyle: {
                color: '#FF005A',
                width: 2
              }
            }
          },
          smooth: true,
          type: 'line',
          data: expectedData,
          animationDuration: 2800,
          animationEasing: 'cubicInOut'
        },
        {
          name: 'actual',
          smooth: true,
          type: 'line',
          itemStyle: {
            normal: {
              color: '#3888fa',
              lineStyle: {
                color: '#3888fa',
                width: 2
              },
              areaStyle: {
                color: '#f3f8ff'
              }
            }
          },
          data: actualData,
          animationDuration: 2800,
          animationEasing: 'quadraticOut'
        }]
      })
    }*/
  }
}
</script>
<style lang="scss" scoped>
.panel-group {
  margin-top: 18px;

  .card-panel-col {
    margin-bottom: 32px;
  }

  .card-panel {
    height: 108px;
    cursor: pointer;
    font-size: 12px;
    position: relative;
    overflow: hidden;
    color: #666;
    background: #fff;
    box-shadow: 4px 4px 40px rgba(0, 0, 0, .05);
    border-color: rgba(0, 0, 0, .05);

    &:hover {
      .card-panel-icon-wrapper {
        color: #fff;
      }

      .icon-people {
        background: #40c9c6;
      }

      .icon-message {
        background: #36a3f7;
      }

      .icon-money {
        background: #f4516c;
      }

      .icon-shopping {
        background: #34bfa3
      }
    }

    .icon-people {
      color: #40c9c6;
    }

    .icon-message {
      color: #36a3f7;
    }

    .icon-money {
      color: #f4516c;
    }

    .icon-shopping {
      color: #34bfa3
    }

    .card-panel-icon-wrapper {
      float: left;
      margin: 14px 0 0 14px;
      padding: 16px;
      transition: all 0.38s ease-out;
      border-radius: 6px;
    }

    .card-panel-icon {
      float: left;
      font-size: 48px;
    }

    .card-panel-description {
      float: right;
      font-weight: bold;
      margin: 26px;
      margin-left: 0px;

      .card-panel-text {
        line-height: 18px;
        color: rgba(0, 0, 0, 0.45);
        font-size: 26px;
        margin-bottom: 12px;
      }

      .card-panel-num {
        font-size: 20px;
      }
    }
  }
}

@media (max-width:550px) {
  .card-panel-description {
    display: none;
  }

  .card-panel-icon-wrapper {
    float: none !important;
    width: 100%;
    height: 100%;
    margin: 0 !important;

    .svg-icon {
      display: block;
      margin: 14px auto !important;
      float: none !important;
    }
  }
}
</style>