<template>
	<div>
		<!-- 头部 -->
		<div class="app-head">
			<div class="app-head-inner">
				<img src="../assets/logo.png">
				<div class="head-nav">
					<ul class="nav-list"> 
						<li> {{ username }}</li>
			            <li v-if="username !== ''" class="nav-pile">|</li>
			            <li v-if="username !== ''" @click="quit">退出</li>
			            <li v-if="username === ''" @click="logClick">登录</li>
						<li v-if="username === ''" class="nav-pile">|</li>
						<li v-if="username === ''" @click="regClick">注册</li>
						<li class="nav-pile">|</li>
						<li @click="aboutClick">关于</li>
					</ul>
				</div> 
			</div>
		</div>

		<!-- 中间内容框 -->
		<div class="app-content">
			<keep-alive>
				 <router-view></router-view>
			</keep-alive>
		</div>

		<!-- 页脚 -->
		<div class="app-foot">
			<p>© 2016 fishenal MIT</p>
		</div>
		
		<!-- dialog组件 - 关于 -->
		<my-dialog :isShow="isShowAboutDialog" @on-close="closeDialog('isShowAboutDialog')">
			<p>about us</p>
		</my-dialog>

		<!-- dialog组件 - 登录  -->
		<my-dialog :isShow="isShowLogDialog" @on-close="closeDialog('isShowLogDialog')">
			<log-form @has-log="onSuccessLog"></log-form>
		</my-dialog>

		<!-- dialog组件 - 注册  -->
		<my-dialog :isShow="isShowRegDialog" @on-close="closeDialog('isShowRegDialog')">
			<reg-form></reg-form>
		</my-dialog>

	</div>
</template>


<script type="text/javascript">

	import Dialog from './dialog'                  //引入dialog组件
	import LogForm from './logForm'                //引入登录组件
	import RegForm from './regForm'			       //引入注册组件

	export default{
		components: {
		    MyDialog: Dialog,                       //dialog组件注册
		    LogForm,                                //登录组件
		    RegForm                                 //注册组件
		},
		data (){
			return {
				isShowAboutDialog : false ,        //dialog的显示隐藏
				isShowLogDialog : false,		   //登录的对话框隐藏
				isShowRegDialog : false,		   //注册的对话框
				username : ""					   //用户名
			}
		},
		methods : {
			aboutClick (){			               //点击关于出现dialog
				this.isShowAboutDialog = true
			},
			closeDialog (attr){                    //关闭dialog对话框
				this[attr] = false 
			},
			logClick (){                           //登录点击
				this.isShowLogDialog = true
			},
			regClick (){                           //注册点击 
				this.isShowRegDialog = true
			},
			onSuccessLog (data){                   // 登录成功
				this.closeDialog ('isShowLogDialog')
				this.username = data.username
			},
			quit (){                               //退出登录
				this.username = ""
			}
		}
	}

</script>

<style>
	/*reset CSS*/
	html, body, div, span, applet, object, iframe,
	h1, h2, h3, h4, h5, h6, p, blockquote, pre,
	a, abbr, acronym, address, big, cite, code,
	del, dfn, em, img, ins, kbd, q, s, samp,
	small, strike, strong, sub, sup, tt, var,
	b, u, i, center,
	dl, dt, dd, ol, ul, li,
	fieldset, form, label, legend,
	table, caption, tbody, tfoot, thead, tr, th, td,
	article, aside, canvas, details, embed, 
	figure, figcaption, footer, header, hgroup, 
	menu, nav, output, ruby, section, summary,
	time, mark, audio, video {
	  	margin: 0;
	  	padding: 0;
	  	border: 0;
	  	font-size: 100%;
	  	font: inherit;
	  	vertical-align: baseline;
	}
	/* HTML5 display-role reset for older browsers */
	article, aside, details, figcaption, figure, 
	footer, header, hgroup, menu, nav, section {
	  	display: block;
	}
	body {
	  	line-height: 1;
	}
	ol, ul {
	  	list-style: none;
	}
	blockquote, q {
	  	quotes: none;
	}
	blockquote:before, blockquote:after,
	q:before, q:after {
	  	content: '';
	  	content: none;
	}
	table {
	  	border-collapse: collapse;
	  	border-spacing: 0;
	}
	a {
	  	color: inherit;
	  	text-decoration: none;
	}
	body {
	  	background: #f0f2f5;
	  	font-family: "Helvetica Neue",Helvetica,Arial,"Hiragino Sans GB","Hiragino Sans GB W3","Microsoft YaHei UI","Microsoft YaHei","WenQuanYi Micro Hei",sans-serif;
	  	font-size: 14px;
	  	color: #444;
	}

	/*header & footer*/
	.app-head {
	  	background: #363636;
	  	color: #b2b2b2;
	  	height: 90px;
	  	line-height: 90px;
	  	width: 100%;
	}
	.app-head-inner {
	  	width: 1200px;
	  	margin: 0 auto;
	}
	.head-logo {
	  	float: left;
	}
	.app-head-inner img {
	  	width: 50px;
	  	margin-top: 20px;
	}
	.head-nav {
	  	float: right;
	}
	.head-nav ul {
	  	overflow: hidden;
	}
	.head-nav li {
	  	cursor: pointer;
	  	float: left;
	}
	.nav-pile {
	  	padding: 0 10px;
	}
	.app-foot {
	  	text-align: center;
	  	height: 80px;
	  	width: 100%;
	  	line-height: 80px;
	  	background: #e3e4e8;
	  	clear: both;
	  	margin-top: 30px;
	}
	.container {
	  	width: 1200px;
	  	margin: 0 auto;
	}
	.hr {
	  	height: 1px;
	  	width: 100%;
	  	background: #ddd;
	}
	.button {
	  	background: #4fc08d;
	  	color: #fff;
	  	display: inline-block;
	  	padding: 10px 20px;
	  	cursor: pointer;
	}
	.button:hover {
	  	background: #4fc08d;
	}
	.g-form-line {
	  	padding: 15px 0;
	}
	.g-form-label {
	  	width: 100px;
	  	font-size: 16px;
	  	display: inline-block;
	}
	.g-form-input {
	 	display: inline-block;
	}
	.g-form-input input {
	  	height: 30px;
	  	width: 200px;
	  	line-height: 30px;
	  	vertical-align: middle;
	  	padding: 0 10px;
	  	border: 1px solid #ccc;
	}
	.g-form-btn {
	  	padding-left: 100px;
	}
	.g-form-error {
	  	color: red;
	  	padding-left: 15px;
	}
</style>