# cc-headerSearch

#### 使用方法 
```使用方法
<!-- icon: 右侧菜单图标 @searchClick：搜索点击  @rigIconClick：右侧菜单点击 -->
<cc-headerSearch icon="../../static/scan.png" @searchClick="searchClick"
@rigIconClick="rigIconClick"></cc-headerSearch>
				
```

#### HTML代码实现部分
```html
<template>
	<view class="content">

		<!-- icon: 右侧菜单图标 @searchClick：搜索点击  @rigIconClick：右侧菜单点击 -->
		<cc-headerSearch icon="../../static/scan.png" @searchClick="searchClick"
			@rigIconClick="rigIconClick"></cc-headerSearch>

		<!--  proList: 条目数组数据  goProDetail:条目点击事件跳转（实现了点击条目数据传值）-->
		<cc-waterListView :proList="projectList" @click="goProDetail"></cc-waterListView>

	</view>
</template>

<script>
	export default {
		data() {
			return {


				// 列表数组
				projectList: []



			}
		},
		onLoad() {
			this.requestData();
		},
		methods: {
			// 列表条目点击事件
			goProDetail(item) {

				console.log("条目数据 = " + JSON.stringify(item));
				uni.showModal({
					title: '选择条目',
					content: '选择条目数据 = ' + JSON.stringify(item)
				})
			},


			requestData() {

				// 模拟请求参数设置
				let reqData = {

					'area': '',
					"pageSize": 10,
					"pageNo": this.curPageNum
				}
				// 模拟请求接口
				this.totalNum = 39;
				this.projectList = [];
				let imgArr = [
					'https://images.pexels.com/photos/4967533/pexels-photo-4967533.jpeg?auto=compress&cs=tinysrgb&w=800',
					'https://cdn.pixabay.com/photo/2014/07/08/14/14/resolution-387446_1280.jpg',
					'https://images.pexels.com/photos/5202162/pexels-photo-5202162.jpeg?auto=compress&cs=tinysrgb&w=800',
					'https://images.pexels.com/photos/4967533/pexels-photo-4967533.jpeg?auto=compress&cs=tinysrgb&w=800',
					'https://images.pexels.com/photos/8679339/pexels-photo-8679339.jpeg?auto=compress&cs=tinysrgb&w=800',
					'https://images.pexels.com/photos/209339/pexels-photo-209339.jpeg?auto=compress&cs=tinysrgb&w=800'
				]

				let nameArr = ['冰糖心苹果 红富士大果出售 应季水果 繁荣种植园', '农鲜洛川红富士苹果16枚，单果160g,新鲜饱满水分充足', '甜醉了 烟台苹果栖霞红富士新鲜水...',
					'惠寻 山东烟台红富士苹果12枚 果径...'
				]
				for (let i = 0; i < 20; i++) {

					this.projectList.push({
						'proImg': imgArr[i % 6],
						'proName': nameArr[i % 4],
						'proDetail': '我是产品详情' + i,
						'proPrice': 60 + 6 * i + '元',
						'status': (i % 3 == 0) ? '618' : '',
						'id': i + ''
					});
				}
			},

			searchClick: function() {

				console.log("点击了搜索框");
				uni.showModal({
					title: '温馨提示',
					content: '点击搜索输入框'
				})


			},
			rigIconClick() {

				console.log("点击了右侧图标");
				uni.showModal({
					title: '温馨提示',
					content: '点击了右侧扫一扫'
				})
			}

		}
	}
</script>

<style>
	page {

		background-color: #f2f2f2;
	}

	.content {
		display: flex;
		flex-direction: column;

	}
</style>



```