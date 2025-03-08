<template>
	<view class="content">
		<div class="langbar">
			<span @click="changeLang('jp')">日本語</span>
			<span @click="changeLang('zh-Hant')">繁體中文</span>
			<span @click="changeLang('zh-Hans')">简体中文</span>
			<span @click="changeLang('en')">English</span>
		</div>
		<img class="logo" src="/static/logo.png"></img>
		<view class="text-area">
			<p>
				<text :class="{titleWakuName:isJp, title:!isJp}">{{msg1}}</text>
				<text :class="{titleWakuName:!isJp, title:isJp}">{{msg2}}</text>
			</p>
		</view>

	</view>
</template>


<script>
	export default {
		data() {
			return {
				title: 'Hello',
				language:'this.$i18n.locale',
				msg1: `${this.$t("waku.greet")}`,
				msg2: `${this.$t("wakuwaku")}`,
				isJp: (this.$i18n.locale==='jp')
			}
		},
		onLoad() {
				console.log(this.isJp)
		},
		methods: {
			changeLang(lang){
				this.$i18n.locale = lang;
				this.language=this.$i18n.locale
				//Change the position and red word for japanese
				if (this.$i18n.locale==='jp'){
					this.isJp= true
					this.msg2= `${this.$t("waku.greet")}`
					this.msg1= `${this.$t("wakuwaku")}`
				}else{
					this.isJp= false
					this.msg1= `${this.$t("waku.greet")}`
					this.msg2= `${this.$t("wakuwaku")}`
				}
			}
		}
	}
</script>

<style scoped>@import url('/css/index.css');</style>
