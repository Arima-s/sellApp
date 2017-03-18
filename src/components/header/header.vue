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
					<span class="support_description"> {{seller.supports[0].description}} </span>
				</div>
			</div>
			<div class="support-count" v-if="seller.supports">
				<span class="count">{{seller.supports.length}}个</span>
				<i class="icon-keyboard_arrow_right"></i>
			</div>
		</div>
		<div class="header_notice">
			<span class="bulletin_bg"></span><span class="bulletin_content">{{seller.bulletin}}</span><i class="icon-keyboard_arrow_right"></i>
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
		color: #fff;
		.header_main {
			width: 100%;
			height: 10.6rem;
			box-sizing: border-box;
			background-color: #757575;
			padding: 2.4rem 1.2rem 1.8rem 2.4rem;
			position: relative;
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
			.support-count{
				padding: .5rem .7rem;
				line-height: 1.5rem;
				position: absolute;
				right: 1.2rem;
				bottom: 1.5rem;
				background-color: rgba(0,0,0,.2);
				border-radius: 18px;
				text-align: center;
				font-size: 1rem;
				line-height: 1.2rem;
				.icon-keyboard_arrow_right{
					vertical-align: middle;
				}
			}
		}
		.header_notice {
			height: 2.8rem;
			overflow: hidden;
			white-space: nowrap;
			text-overflow: ellipsis;
			background-color: rgba(7,17,27,.2);
			font-size: 1rem;
			line-height: 2.8rem;
			font-weight: 200;
			padding: 0 2rem 0 1rem;
			position: relative;
			.bulletin_bg {
				display: inline-block;
        vertical-align: top;
				width: 2.2rem;
        height: 1.2rem;
        font-size: 1rem;
        margin-top: .7rem;
        margin-right: .5rem;
				@include bg-image('bulletin');
				background-size: 100% 100%;
				background-repeat: no-repeat;
			}
			.icon-keyboard_arrow_right {
				position: absolute;
				right: .5rem;
				top: .9rem;
				font-size: 1rem;
				vertical-align: middle;
			}
		}
		
	}
</style>