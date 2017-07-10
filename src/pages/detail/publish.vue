<template>
  	<div class="sales-board">
      	<div class="sales-board-intro">
        	<h2>广告发布</h2>
        	<p>广告活动按照广告计划执行，到完成广告创作并形成广告作品之后，经过广告主的最后审核同意，即可送到预定的媒介发布刊播。这项工作一般由媒介部门的有关专业人员负责，他们的任务就是专门负责与有关媒介单位接洽，安排有关广告的发播事宜，并对发播质量实施监督。</p>
      	</div>
      	<div class="sales-board-form">
          	<div class="sales-board-line">
              	<div class="sales-board-line-left">
                  	购买数量：
              	</div>
              	<div class="sales-board-line-right">
                  	<v-counter :max="100" :min="20"></v-counter>
              	</div>
          	</div>
          	<div class="sales-board-line">
              	<div class="sales-board-line-left">
                  	行业：
              	</div>
              	<div class="sales-board-line-right">
                  	<v-selection :selections="tradeList"></v-selection>
              	</div>
          	</div>
          	<div class="sales-board-line">
              	<div class="sales-board-line-left">
                  	产品版本：
              	</div>
              	<div class="sales-board-line-right">
                  	<v-mul-chooser :selections="versionList"></v-mul-chooser>
              	</div>
          	</div>
          	<div class="sales-board-line">
              	<div class="sales-board-line-left">
                  	有效时间：
              	</div>
              	<div class="sales-board-line-right">
                  	半年
              	</div>
          	</div>
          	<div class="sales-board-line">
              	<div class="sales-board-line-left">
                  	总价：
              	</div>
              	<div class="sales-board-line-right">
                  	500 元
              	</div>
          	</div>
          	<div class="sales-board-line">
              	<div class="sales-board-line-left">&nbsp;</div>
              	<div class="sales-board-line-right">
                  	<div class="button">
                    	立即购买
                  	</div>
              	</div>
          	</div>
      	</div>
      	<div class="sales-board-des">
        	<h2>产品说明</h2>
        	<p>广告活动按照广告计划执行，到完成广告创作并形成广告作品之后，经过广告主的最后审核同意，即可送到预定的媒介发布刊播。这项工作一般由媒介部门的有关专业人员负责，他们的任务就是专门负责与有关媒介单位接洽，安排有关广告的发播事宜，并对发播质量实施监督。</p>

        	<table class="sales-board-table">
	          	<tbody>
	              	<tr class="ui-table-row">
	                  	<td class="col-first">
	                      	<div class="intro-pic">
	                          	<label>安全安保</label>
	                      	</div>
	                  	</td>
	                  	<td>
	                      	<div class="intro-pic">
	                          	<label>办公文教</label>
	                      	</div>
	                  	</td>
	                  	<td>
	                      	<div class="intro-pic">
	                          	<label>彩票</label>
	                      	</div>
	                  	</td>
	                  	<td>
	                      	<div class="intro-pic">
	                          	<label>车辆物流</label>
	                      	</div>
	                  	</td>
	                  	<td>
	                      	<div class="intro-pic">
	                          	<label>成人用品</label>
	                      	</div>
	                  	</td>
	                  	<td>
	                      	<div class="intro-pic">
	                          	<label>出版传媒</label>
	                      	</div>
	                  	</td>
	                  	<td>
	                      	<div class="intro-pic">
	                          	<label>电脑硬件</label>
	                      	</div>
	                  	</td>
	              	</tr>
						              	<tr class="ui-table-row">
	                  	<td class="col-first">
	                      	<div class="intro-pic">
	                          	<label>安全安保</label>
	                      	</div>
	                  	</td>
	                  	<td>
	                      	<div class="intro-pic">
	                          	<label>办公文教</label>
	                      	</div>
	                  	</td>
	                  	<td>
	                      	<div class="intro-pic">
	                          	<label>彩票</label>
	                      	</div>
	                  	</td>
	                  	<td>
	                      	<div class="intro-pic">
	                          	<label>车辆物流</label>
	                      	</div>
	                  	</td>
	                  	<td>
	                      	<div class="intro-pic">
	                          	<label>成人用品</label>
	                      	</div>
	                  	</td>
	                  	<td>
	                      	<div class="intro-pic">
	                          	<label>出版传媒</label>
	                      	</div>
	                  	</td>
	                  	<td>
	                      	<div class="intro-pic">
	                          	<label>电脑硬件</label>
	                      	</div>
	                  	</td>
	              	</tr>
	              		              	<tr class="ui-table-row">
	                  	<td class="col-first">
	                      	<div class="intro-pic">
	                          	<label>安全安保</label>
	                      	</div>
	                  	</td>
	                  	<td>
	                      	<div class="intro-pic">
	                          	<label>办公文教</label>
	                      	</div>
	                  	</td>
	                  	<td>
	                      	<div class="intro-pic">
	                          	<label>彩票</label>
	                      	</div>
	                  	</td>
	                  	<td>
	                      	<div class="intro-pic">
	                          	<label>车辆物流</label>
	                      	</div>
	                  	</td>
	                  	<td>
	                      	<div class="intro-pic">
	                          	<label>成人用品</label>
	                      	</div>
	                  	</td>
	                  	<td>
	                      	<div class="intro-pic">
	                          	<label>出版传媒</label>
	                      	</div>
	                  	</td>
	                  	<td>
	                      	<div class="intro-pic">
	                          	<label>电脑硬件</label>
	                      	</div>
	                  	</td>
	              	</tr>
	              		              	<tr class="ui-table-row">
	                  	<td class="col-first">
	                      	<div class="intro-pic">
	                          	<label>安全安保</label>
	                      	</div>
	                  	</td>
	                  	<td>
	                      	<div class="intro-pic">
	                          	<label>办公文教</label>
	                      	</div>
	                  	</td>
	                  	<td>
	                      	<div class="intro-pic">
	                          	<label>彩票</label>
	                      	</div>
	                  	</td>
	                  	<td>
	                      	<div class="intro-pic">
	                          	<label>车辆物流</label>
	                      	</div>
	                  	</td>
	                  	<td>
	                      	<div class="intro-pic">
	                          	<label>成人用品</label>
	                      	</div>
	                  	</td>
	                  	<td>
	                      	<div class="intro-pic">
	                          	<label>出版传媒</label>
	                      	</div>
	                  	</td>
	                  	<td>
	                      	<div class="intro-pic">
	                          	<label>电脑硬件</label>
	                      	</div>
	                  	</td>
	              	</tr>
	              		              	<tr class="ui-table-row">
	                  	<td class="col-first">
	                      	<div class="intro-pic">
	                          	<label>安全安保</label>
	                      	</div>
	                  	</td>
	                  	<td>
	                      	<div class="intro-pic">
	                          	<label>办公文教</label>
	                      	</div>
	                  	</td>
	                  	<td>
	                      	<div class="intro-pic">
	                          	<label>彩票</label>
	                      	</div>
	                  	</td>
	                  	<td>
	                      	<div class="intro-pic">
	                          	<label>车辆物流</label>
	                      	</div>
	                  	</td>
	                  	<td>
	                      	<div class="intro-pic">
	                          	<label>成人用品</label>
	                      	</div>
	                  	</td>
	                  	<td>
	                      	<div class="intro-pic">
	                          	<label>出版传媒</label>
	                      	</div>
	                  	</td>
	                  	<td>
	                      	<div class="intro-pic">
	                          	<label>电脑硬件</label>
	                      	</div>
	                  	</td>
	              	</tr>
	          </tbody>
	      </table>
      </div>
  </div>
</template>
<script>

	import VSelection from '../../components/selection'
	import VCounter from '../../components/counter'
	import VMulChooser from '../../components/multiplyChooser'

    export default {
    	components : {
    		VSelection,
    		VCounter,
    		VMulChooser
    	},
        data () {
            return {
          		tradeList: [
			        {
			          	label: '出版业',
			          	value: 0
			        },
			        {
			          	label: '媒体',
			          	value: 1
			        },
			        {
			          	label: '金融',
			          	value: 2
			        },
			        {
			          	label: '互联网',
			          	value: 3
			        },
			        {
			          	label: '游戏',
			          	value: 4
			        }
			    ],
			    versionList: [
			        {
			          	label: '初级版',
			          	value: 0
			        },
			        {
			          	label: '中级版',
			          	value: 1
			        },
			        {
			          	label: '高级版',
			          	value: 2
			        },
			        {
			          	label: '专家版',
			          	value: 3
			        }
			    ]
            }
        }
    }

</script>

<style scoped>

</style>
