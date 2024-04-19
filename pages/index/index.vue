<template>
	<view class="content">
		<!-- demo -->
		<scroll-view class="top" scroll-x="true" :scroll-left="left" @scroll="handleScrollTop">
			<view class="list" v-for="i in 10" :key="i">
				薄膜#{{i}}
			</view>
		</scroll-view>
		<scroll-view scroll-y="true" class="left" @scroll="handleScrollLeft" :scroll-top="top">
			<view class="list" v-for="i in 10" :key="i">
				属性{{i}}
			</view>
		</scroll-view>
		<view class="content">
			<scroll-view class="scroll" scroll-y="true" scroll-x="true" :scroll-left="left" :scroll-top="top"
				@scroll="handleScrollContent">
				<table border="1">
					<tbody>
						<tr v-for="i in 10" :key="i">
							<td v-for="j in 10" :key="j">
								<view class="span">
									<view class="btn" @click="btn(i,j,'合格')">
										{{j}}-{{i}}合格
									</view>
									<view class="btn" @click="btn(i,j,'不合格')">
										{{j}}-{{i}}不合格
									</view>
								</view>
							</td>
						</tr>

					</tbody>
				</table>
			</scroll-view>
		</view>
	</view>
</template>

<script>
	import debounce from '../../utils/utils';
	export default {
		data() {
			return {
				top: 0,
				left: 0
			}
		},
		onLoad() {},

		methods: {
			// handleScrollContent(event) {
			// 	this.top = event.detail.scrollTop;
			// 	this.left = event.detail.scrollLeft;
			// },
			// handleScrollTop(event){
			// 	this.left = event.detail.scrollLeft;
			// },
			// handleScrollLeft(event){
			// 	this.top = event.detail.scrollTop;
			// },

			handleScrollContent: debounce(function(event) {
				this.top = event.detail.scrollTop;
				this.left = event.detail.scrollLeft;
			}, 100),
			handleScrollTop: debounce(function(event) {
					this.left = event.detail.scrollLeft;
			}, 100),
			handleScrollLeft: debounce(function(event) {
					this.top = event.detail.scrollTop;
			}, 100),


			btn(i, j, info) {
				console.log(`您点击了薄膜${j},属性${i},${info}`);
			}
		}
	}
</script>

<style scoped lang="scss">
	@import "css/index.scss";
</style>