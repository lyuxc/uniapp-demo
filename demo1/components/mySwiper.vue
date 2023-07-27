<template>
	<view class="swiper-container">
		<view class="uni-margin-wrap">
			<swiper class="swiper" circular :indicator-dots="indicatorDots" :autoplay="autoplay" :interval="interval"
				:duration="duration">
				<swiper-item v-for="val in list">
					<view class="swiper-item">
						<img :src="val.topicImgUrl">
						<view class="title">{{val.title}}</view>
					</view>
				</swiper-item>
			</swiper>
		</view>
	</view>
</template>

<script>
	export default {
		name:"mySwiper",
		data() {
			return {
				background: ['color1', 'color2', 'color3'],
				indicatorDots: true,
				autoplay: true,
				interval: 5000,
				duration: 500,
				list: []
			};
		},
		mounted() {
			console.log('swiper-mounted')
			uni.request({
			    url: 'https://gw-api-hk-di1.sit.cmft.com/chslas/v1/articleCH/carousels?businessId=15707f4df7ac84593a87bc14854a3bfb&templateId=2',
			    // data: {
			    //     text: 'uni.request'
			    // },
			    // header: {
			    //     'custom-header': 'hello' //自定义请求头信息
			    // },
			    success: (res) => {
			        console.log(res);
			        this.list = res.data.body
			    }
			});
		}
	}
</script>

<style lang="scss">
	.swiper-container {
		.uni-margin-wrap {
		}
		.swiper {
			height: 400rpx;
			width: 750rpx;
		}
		.swiper-item {
			display: block;
			text-align: center;
			position: relative;
			.title {
				position: absolute;
				bottom: 20px;
				color: #fff;
				font-size: 16px;
				overflow: hidden;
				text-overflow: ellipsis;
				white-space: nowrap;
				width: 700rpx;
				padding-left: 20rpx;
			}
			img {
				max-width: 100%;
				height: auto;
			}
		}
	}
</style>