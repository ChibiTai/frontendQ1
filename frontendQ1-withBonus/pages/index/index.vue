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
				<text v-if="language==='jp'" class="titleWakuName">{{ $t("wakuwaku") }}</text>
				<text class="title">{{ $t("waku.greet") }}&nbsp</text>
				<text v-if="language!='jp'"class="titleWakuName">{{ $t("wakuwaku") }}</text>
			</p>
		</view>

	</view>
</template>


<script>
	export default {
		data() {
			return {
				title: 'Hello',
				language:'this.$i18n.locale'
			}
		},
		onLoad() {

		},
		methods: {
			changeLang(lang){
				this.$i18n.locale = lang;
				this.language=this.$i18n.locale
			},
		}
	}
</script>

<style scoped>@import url('/css/index.css');</style>
