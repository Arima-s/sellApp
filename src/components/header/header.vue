<template>
	<div class="header">
		<div class="header_main">
			<div class="header_avatar">
				<img :src="seller.avatar" alt="商家头像">
			</div>
			<div class="content">
				<div class="title">
					<span class="seller_brand"></span>
					<span class="seller_name">{{seller.name}}</span>
				</div>
				<div class="description">
					{{seller.description}}/{{seller.deliveryTime}}分钟送达
				</div>
				<div class="supports" v-if="seller.supports" >
					<span class="support_brand" :class="classMap[seller.supports[0].type]"></span>
					<span class="support_description">{{seller.supports[0].description}}</span>
				</div>
			</div>
		</div>
		<div class="header_notice">
			
		</div>
	</div>
</template>

<script type="text/ecmascript-6">
	export default {
		props: {
			seller: {
				type: Object
			}
		},
		created() {
			this.classMap = ['decrease', 'discount', 'guarantee', 'invoice', 'special'];
		}
	};
</script>

<style lang="scss">

  @import "../../common/scss/mixin.scss";

	.header {
		width: 100%;
		height: 13.4rem;
		background-color: skyblue;
		color: #fff;
		.header_main {
			width: 100%;
			height: 10.6rem;
			box-sizing: border-box;
			background-color: #757575;
			padding: 2.4rem 1.2rem 1.8rem 2.4rem;
			.header_avatar {
				float: left;
				width: 6.4rem;
				height: 100%;
				box-sizing: border-box;
				margin-right: 1.6rem;
				border-radius: .2rem;
				overflow: hidden;
				img {
					width: 6.4rem;
					height: 6.4rem;
				}
			}
			.content {
				float: left;
				color: rgb(255,255,255);
				.title {
					margin: .2rem 0 .8rem 0;
					.seller_brand {
						display: inline-block;
						vertical-align: top;
						width: 3rem;
						height: 1.8rem;
						@include bg-image('brand');
						background-size: 100% 100%;
						background-repeat: no-repeat;
					}
					.seller_name{
						font-size: 1.6rem;
						line-height: 1.8rem;
						color: rgb(255,255,255);
						font-weight: bold;
					}
				}
				.description {
					font-size: 1.2rem;
					line-height: 1.2rem;
					margin-bottom: 1rem;
				}
				.supports{
					font-size: 0;
					.support_brand{
						display: inline-block;
						vertical-align: top;
            width: 1.2rem;
            height: 1.2rem;
            margin-right: .4rem;
            background-size: 1.2rem 1.2rem;
            background-repeat: no-repeat;
            &.decrease {
              @include bg-image('decrease_1');
            }
            &.discount{
              @include bg-image('discount_1');
            }
            &.guarantee{
              @include bg-image('guarantee_1');
            }
            &.invoice{
              @include bg-image('invoice_1');
            }
            &.special{
              @include bg-image('special_1');
            }
					}
					.support_description{
						line-height: 1.2rem;
						font-size: 1rem;
					}
				}
			}
		}
		
	}
</style>