<template>

	<view class="navBar">

		<!-- 搜索框 -->
		<view class="search_box">
			
			<view class="searchBg">
				<view class="input-box" @tap="jumpSearch">
					<input placeholder="搜索内容" class="inputs" disabled
						placeholder-style="color:#c0c0c0;font-size:24upx;"></input>
					<view class="icon searchBg">
						<image src="./search.png" class="search_img"></image>
					</view>
				</view>
			</view>
		</view>

		<!-- 右侧按钮 -->
		<view class="hierarchy" @tap="rigMenuClick">

			<image class="imgV" mode="aspectFit" :src="icon"></image>

		</view>

	</view>

</template>

<script>
	export default {
		data() {
			return {};
		},

		
		props: {
			
			// 菜单图标
			icon: {
				type: String,
				default: '',
			}
			
		},
		methods: {
			jumpSearch() {
				
				this.$emit("searchClick");
			},
			
			rigMenuClick(){
				
				this.$emit("rigIconClick");
			}

		}
	};
</script>
<style lang="scss" scoped>
	.navBar {
		padding: 20px 3% 0px 3%;
		display: flex;
		overflow: hidden;
		align-items: center;
		justify-content: space-between;
		width: 94%;
		background-color: white;
	}

	.search_box {
		width: 90%;
	}

	.hierarchy {
		width: 10%;
		height: 60upx;
		font-size: 32upx;
		text-align: right;
	}

	.imgV {

		width: 24px;
		height: 24px;
	}

	// 搜索框背景
	.searchBg {
		z-index: 900;
		display: flex;
		flex-direction: column;
	}


	.input-box {
		width: 100%;
		height: 60upx;
		background-color: #f5f5f5;
		position: relative;
		display: flex;
		align-items: center;
		border-radius: 30upx;
		margin-bottom: 20upx;
		z-index: 900;
	}

	.input-box .icon {
		display: flex;
		align-items: center;
		position: absolute;
		top: 10upx;
		right: 20upx;
		width: 40upx;
		height: 40upx;
		font-size: 32upx;
		color: #c0c0c0;
	}

	.searchBg .search_img {
		width: 40upx;
		height: 40upx;
		display: block;
	}

	.input-box .inputs {
		padding-left: 28upx;
		height: 28upx;
		font-size: 28upx;
	}
</style>