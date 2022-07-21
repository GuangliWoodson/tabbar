<template>
	<table class="table table-bordered table-stripped">
		<!-- 表格标题区域 -->
		<thead>
			<tr>
				<!-- <th>#</th>
				<th>商品名称</th>
				<th>价格</th>
				<th>标签</th>
				<th>操作</th> -->
				<slot name="header"></slot>
      </tr>
    </thead>
    <!-- 表格主体区域 -->
    <tbody>
      <tr v-for="(item, index) in arr"  :key="item.id">
					<!-- <td>{{ item.id }}</td>
					<td>{{ item.goods_name }}</td>
					<td>{{ item.goods_price }}</td>
					<td>{{ item.goods_tags }}</td>
					<td>
						<button class="btn btn-danger btn-sm">delete</button>
					</td> -->
					<slot name="body" :row="item" :index="index"></slot>
			</tr>
			</tbody>
	</table>
</template>

<script>
export default {
	props: {
		arr: {
			type: Array,
			default: () => { }
		},
	},

}
</script>


<style scoped lang="less">
.my-goods-list {
	.badge {
		margin-right: 5px;
	}
}
</style>