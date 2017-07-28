<template>
	<nav class="pages clearfix">
		<!-- 分页组件 -->
		<ul class="pagination clearfix">
			<template v-if="perRows<totalCount">
				<router-link :to="{name: listname,  params: { p: pageNum-1<1?1:pageNum-1}}" tag="li"><a href="">上一页</a></router-link>
				<router-link :to="{name: listname,  params: { p: 1}}" tag="li" exact><a href="">1</a></router-link>
				<!-- 判断页数小于10 -->
				<template v-if="Math.ceil(totalCount/perRows)<=10">
					<template v-for="v in Math.ceil(totalCount/perRows)">
						<router-link :to="{name: listname,  params: { p: v}}" v-if="v>1 && v< Math.ceil(totalCount/perRows)" tag="li" append><a href="">{{v}}</a></router-link>
					</template>
				</template>
				<!-- 判断页数大于10 -->
				<template v-if="Math.ceil(totalCount/perRows)>10">
					<li v-if="pageNum > 2"><span>...</span></li>
					<template v-for="v in Math.ceil(totalCount/perRows)">
						<router-link :to="{name: listname,  params: { p: v}}" v-if="v>1 && v>(pageNum-3) && v< (pageNum+3) && v< Math.ceil(totalCount/perRows)" tag="li" append><a href="">{{v}}</a></router-link>
					</template>
					<li v-if="pageNum < Math.ceil(totalCount/perRows)-1"><span>...</span></li>
				</template>

				<router-link :to="{name: listname,  params: { p: Math.ceil(totalCount/perRows)}}" tag="li" exact><a href="">{{Math.ceil(totalCount/perRows)}}</a></router-link>	
				<router-link :to="{name: listname,  params: { p: pageNum+1>Math.ceil(totalCount/perRows)?Math.ceil(totalCount/perRows):pageNum+1}}" tag="li"><a href="">下一页</a></router-link>
			</template>
			<li><span>共{{totalCount}}条,共{{Math.ceil(totalCount/perRows)}}页</span></li>
		</ul>
	</nav>
</template>
<script>
	export default {
		data () {
			return {
	
			}
		},
		// props: ['pageNum','perRows','totalCount','listname'] //pageNum当前页 perRows每页显示多少数据 totalCount总条数 listname分页模块路由名
		// 传递给分页组件数据的时候 如果两次传递的数据相同 那么分页组件则不会有任何变化 这时候需要在传递准确数据前传递一次无效数据 --- 主要用于多种条件排序切换时的情况
		props: {
			pageNum: {
				default: 1
			},
			perRows: {
				default: 10
			},
			totalCount: {
				default: 0
			},
			listname: {
				default: ''
			}
		},
		mounted () {
			
		}
	}
</script>
