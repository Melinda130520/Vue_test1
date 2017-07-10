<template>
    <div class="counter-component">
      	<div class="counter-btn" @click="minus"> - </div>
      	<div class="counter-show">
        	<input type="text" v-model="number" @keyup="fixNumber" @blur="resetNumber">
      	</div>
      	<div class="counter-btn" @click="add"> + </div>
    </div>
</template>


<script type="text/javascript">
	export default{
		//从父组件中获取参数
		props: {    
		    max: {    //可购买的最大值
		      	type: Number,
		      	default: 5
		    },
		    min: {    //可购买的最小值
		      	type: Number,
		      	default: 1
		    }
		},
		data (){
			return {
				number : this.min     //购物车数量初始值为可购买的最小值
			}
		},
		watch : {
			//购买数量发生变化的时候传统给父组件
			number (){
				this.$emit('on-change', this.number)    
			}
		},
		methods : {
			// 填写购物车数量
			fixNumber (){
				let fix

				if(this.number.length === 0) {
					this.number = '';
					return;
				}

				// 判断输入是否含有字母类，将非数字替换成空，然后再转化为Number类型
				fix = Number(String(this.number).replace(/\D/g, ''))

				this.number = fix
			},
			// 失去焦点重置最小值
			resetNumber (){
				if(this.number === '' || this.number > this.max || this.number < this.min) {
					this.number = this.min;
				}
			},
			// 减少购物车数量
			minus (){
				if (this.number <= this.min) {
			        return
			    }
			    this.number --
			},
			// 增加购物车数量
			add (){     
				if (this.number >= this.max) {
			        return
			    }
			    this.number ++
			}
		}
	}
</script>

<style scoped>
	.counter-component {
	  	position: relative;
	  	display: inline-block;
	  	overflow: hidden;
	  	vertical-align: middle;
	}
	.counter-show {
	  	float: left;
	}
	.counter-show input {
	  	border: none;
	  	border-top: 1px solid #e3e3e3;
	  	border-bottom: 1px solid #e3e3e3;
	  	height: 23px;
	  	line-height: 23px;
	  	width: 30px;
	  	outline: none;
	  	text-indent: 4px;
	}
	.counter-btn {
	  	border: 1px solid #e3e3e3;
	  	float: left;
	  	height: 25px;
	  	line-height: 25px;
	  	width: 25px;
	  	text-align: center;
	  	cursor: pointer;
	}
	.counter-btn:hover {
	  	border-color: #4fc08d;
	  	background: #4fc08d;
	  	color: #fff;
	}
</style>