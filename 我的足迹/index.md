---
title: 我的足迹
date: 2017-09-04 15:30:46
---
<script type="text/javascript" src="http://echarts.baidu.com/gallery/vendors/echarts/echarts.min.js"></script>
<script type="text/javascript" src="http://echarts.baidu.com/gallery/vendors/echarts/map/js/china.js"></script>

	
<div id="Map" style="height: 500px">
		<!--这以后是地图-->
</div>
	
<script type="text/javascript">
  var Echartsmap=echarts.init(document.getElementById("Map"));
	var city = [
     {name: '青岛', value: 200},
     {name: '泉州', value: 200},
     {name: '上海', value: 200},
     {name: '威海', value: 200},
     {name: '厦门', value: 200},
     {name: '宁波', value: 200},
     {name: '昆明', value: 200},
     {name: '咸阳', value: 200},
     {name: '西宁', value: 200},
     {name: '西安', value: 200},
     {name: '南京', value: 200},
     {name: '北京', value: 200},
     {name: '杭州', value: 200},
     {name: '济南', value: 200},
     {name: '临沂', value: 200},
     {name: '郑州', value: 200},
     {name: '济宁', value: 200},
     {name: '武汉', value: 200},
     {name: '丽江', value: 200},
     {name: '西双版纳', value: 200},
     {name: '大理', value: 200},
     {name: '深圳', value: 200},

     {name:'茶卡盐湖',value:100},
     {name:'青海湖',value:100},
     {name:'东方明珠',value:100},
     {name:'五四广场',value:100},
     {name:'中科院西双版纳热带植物园',value:100},
     {name:'刘公岛',value:100},
     {name:'塔尔寺',value:100},
     {name:'大雁塔',value:100},
     {name:'骊山',value:100},
     {name:'鼓浪屿',value:100},
     {name:'玉龙雪山',value:100},
     {name:'丽江古城',value:100},
     {name:'西湖',value:100},
     {name:'蒙山',value:100},
     {name:'拉市海',value:100},
     {name:'束河古镇',value:100},
     {name:'大理古城',value:100},
     {name:'崇圣寺三塔公园',value:100},
     {name:'洱海',value:100},
     {name:'夫子庙',value:100},
     {name:'天安门广场',value:100},
     {name:'故宫',value:100},
     {name:'黄鹤楼',value:100},
     {name:'十渡风景区',value:100},
     {name:'大明湖',value:100},
     {name:'趵突泉',value:100},
     {name:'八大关',value:100},
     {name:'金沙滩',value:100},
];
 
var geoCoordMap = {
    '青岛':[120.33,36.07],
    '泉州':[118.58,24.93],
    '上海':[121.48,31.22],
    '威海':[122.1,37.5],
    '厦门':[118.1,24.46],
    '宁波':[121.56,29.86],
    '昆明':[102.73,25.04],
    '咸阳':[108.72,34.36],
    '西宁':[101.74,36.56],
    '西安':[108.95,34.27],
    '南京':[118.78,32.04],
    '北京':[116.46,39.92],
    '杭州':[120.19,30.26],
    '济南':[117,36.65],
    '临沂':[118.35,35.05],
    '郑州':[113.65,34.76],
    '济宁':[116.59,35.38],
    '武汉':[114.31,30.52], 
    '丽江':[100.23331,26.884395], 
    '西双版纳':[100.79816,22.014105], 
    '大理':[100.237692,25.597645], 
    '深圳':[114.138509,22.556972],

    '茶卡盐湖':[99.101084,36.749992],
    '青海湖':[100.187498,36.866642],
    '东方明珠':[121.506377,31.245105],
    '五四广场':[120.391729,36.067581],
    '中科院西双版纳热带植物园':[101.271188,21.923736],
    '刘公岛':[122.197255,37.511219],
    '塔尔寺':[101.576298,36.494462],
    '大雁塔':[108.970492,34.229142],
    '骊山':[109.221086,34.364599],
    '鼓浪屿':[118.071909,24.456348],
    '玉龙雪山':[100.270093,27.034013],
    '丽江古城':[100.241894,26.876504],
    '西湖':[120.156352,30.251713],
    '蒙山':[117.98073,35.565713],
    '拉市海':[100.145784,26.896587],
    '束河古镇':[100.212875,26.926349],
    '大理古城':[100.172117,25.698864],
    '崇圣寺三塔公园':[100.155887,25.711798],
    '洱海':[100.272671,25.649292],
    '夫子庙':[118.795264,32.027003],
    '天安门广场':[116.404168,39.909677],
    '故宫':[116.402122,39.929583],
    '黄鹤楼':[114.309052,30.550239],
    '十渡风景区':[115.606468,39.644162],
    '大明湖':[117.029409,36.680642],
    '趵突泉':[117.022388,36.667454],
    '八大关':[120.357644,36.059717],
    '金沙滩':[120.25126,35.964533],
};


var convertData = function (city) {
    var res = [],res2=[];
    for (var i = 0; i < city.length; i++) {
        var geoCoord = geoCoordMap[city[i].name];
        if (geoCoord) {
            res.push({
                name: city[i].name,
                value: geoCoord.concat(city[i].value)
            });
        }
    }

    res2=res.filter( function (a) {
        return a.value[2]==200;
    });
    return res2;
};

var convertDataSpot = function (city) {
    var res = [],res2=[];
    for (var i = 0; i < city.length; i++) {
        var geoCoord = geoCoordMap[city[i].name];
        if (geoCoord) {
            res.push({
                name: city[i].name,
                value: geoCoord.concat(city[i].value)
            });
        }
    }

      res2=res.filter( function (a) {
        return a.value[2]==100;
    });
    return res2;
};

option = {
    backgroundColor: '#404a59',
    title: {
        text: '路途',
        subtext: '去过的或者待过的地方',       
        left: 'center',
        textStyle: {
            color: '#fff'
        }
    },
    tooltip : {
        trigger: 'item' //触发类型。数据项图形触发，主要在散点图，饼图等无类目轴的图表中使用。
    },
    legend: {   //图例组件。
        orient: 'vertical',
        y: 'bottom',
        x:'right',
        data:['景点','City'],
        // 设置文本颜色
        textStyle: {
            color: '#fff'
        }
    },
    geo: {
        map: 'china',
        label: {
            emphasis: {
                show: false
            }
        },
        roam: true,//缩放拖动打开
        itemStyle: {
            normal: {
                areaColor: '#323c48',
                borderColor: '#111'
            },
            emphasis: {
                areaColor: '#2a333d'
            }
        }
    },
    series : [
        {
            name: '景点',
            type: 'scatter',//散点（气泡）图
            coordinateSystem: 'geo',
            data: convertDataSpot(city),
            symbolSize: 10,
            
            label: {
                normal: {
                    formatter: '{b}',
                    position: 'right',
                    show: false
                },
                emphasis: {
                    show: true
                }
            },
            itemStyle: {
                normal: {
                    color: '#00FFFF'
                }
            }
        },
        {
            name: 'City',
            type: 'effectScatter',//涟漪特效动画的散点（气泡）图
            coordinateSystem: 'geo',
            data:  convertData(city),
            //标志的大小
            symbolSize: 15,
             showEffectOn: 'render',
            rippleEffect: {
                brushType: 'stroke'
            },
            hoverAnimation: true,
            label: {
                normal: {
                    formatter: '{b}',
                    position: 'right',
                    show: true
                },
                emphasis: {
                    show: true
                }
            },
            itemStyle: {
                normal: {
                    color: '#f4e925',
                    shadowBlur: 10,
                    shadowColor: '#333'
                }
            },
            zlevel: 2
        }
       
    ]
};

Echartsmap.setOption(option);
</script>
