<template>
	<div>
		<MyTable :arr="list">
			<template #header>
				<th>#</th>
				<th>商品名称</th>
				<th>价格</th>
				<th>标签</th>
				<th>操作</th>
			</template>

			<template #body="scope">
				<td>{{ scope.row.id }}</td>
				<td>{{ scope.row.goods_name }}</td>
				<td>{{ scope.row.goods_price }}</td>
				<td>
					<input type="text" class="tag-input form-control" style="width: 100px" v-if="scope.row.inputVisible" v-focus
						@blur="scope.row.inputVisible = false" @keyup.enter="addFn(scope.row)" @keyup.esc="scope.row.inputValue = ''"
						v-model="scope.row.inputValue" />
					<button v-else class="btn btn-primary btn-sm add-tag" @click="scope.row.inputVisible = true">
						+Tag
					</button>
					<span v-for="(item, index) in scope.row.tags" :key="index" class="badge badge-warning">
						{{ item }}
					</span>
				</td>
				<td>
					<button class="btn btn-danger btn-sm" @click="del(scope.row.id)">delete</button>
				</td>
			</template>
		</MyTable>
	</div>
</template>

<script>
import MyTable from "../components/MyTable";

export default {
	components: {
		MyTable,
	},
	data() {
		return {
			list: []
		};
	},
	created() {
		this.$axios({
			url: "/api/goods",
		}).then((res) => {
			this.list = res.data.data;
		}).catch((err) => {
			console.log(err);
		});
	},
	methods: {
		del(id) {
			const index = this.list.findIndex(item => item.id === id)
			this.list.splice(index, 1)
		},
		addFn(val) {
			if (val.inputValue.trim().length === 0) {
				alert("Please enter a value");
				return
			}
			val.tags.push(val.inputValue)
			val.inputValue = ""
		}
	}
};
</script>