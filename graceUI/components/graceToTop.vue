<template>
	<view class="grace-totop" v-if="show" @tap="totop">
		<text class="totopfont icon-top" :style="{color:color}"></text>
	</view>
</template>
<script>
export default{
	props:{
		top : {
			type : Number,
			default : 0
		},
		color : {
			type : String,
			default : "#3688FF"
		}
	},
	data() {
		return {
			show : false,
			timer : null
		}
	},
	watch:{
		top : function(topVal){
			if(this.timer != null){clearTimeout(this.timer);}
			this.timer = setTimeout(function(){
				if(topVal > 100){
					this.show = true;
				}else{
					this.show = false;
				}
			}.bind(this), 80);
		}
	},
	methods:{
		totop : function(){
			uni.pageScrollTo({
				scrollTop: 0,
				duration: 0
			});
		}
	}
}
</script>
<style>
@font-face {font-family:"gFont"; src:url('https://at.alicdn.com/t/font_1348803_h8kl243o7ol.ttf') format('truetype');}
.totopfont {
  font-family: "gFont" !important;
  font-style: normal;
}
.icon-top:before { content: "\e600"; font-size:22px;}
.grace-totop{width:40px; height:40px; line-height:40px; background:#FFFFFF; color:#3688FF; position:fixed; bottom:80px; z-index:9999; right:15px; border-radius:5px; box-shadow:0px 0px 2px #EEE; text-align:center;}
</style>