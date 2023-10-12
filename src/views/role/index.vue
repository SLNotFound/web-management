<template>
  <div class="container">
    <div class="app-container">
      <!-- 角色管理 -->
      <div class="role-operate">
        <el-button size="mini" type="primary">添加角色</el-button>
      </div>
      <el-table :data="list">
        <el-table-column prop="name" align="center" width="200" label="角色" />
        <el-table-column prop="state" align="center" width="200" label="启用">
          <template v-slot="{ row }">
            <span>{{ row.state === 1 ? "已启用" : row.state === 0 ? "未启用" : "无" }}</span>
          </template>
        </el-table-column>
        <el-table-column prop="description" align="center" label="描述" />
        <el-table-column align="center" label="操作">
          <template>
            <el-button size="mini" type="text">分配权限</el-button>
            <el-button size="mini" type="text">编辑</el-button>
            <el-button size="mini" type="text">删除</el-button>
          </template>
        </el-table-column>
      </el-table>
      <el-row type="flex" style="height:60px" align="middle" justify="end">
        <el-pagination layout="prev, pager, next" />
      </el-row>
    </div>
  </div>
</template>
<script>
import { getRoleList } from '@/api/role'
export default {
  name: 'Role',
  data() {
    return {
      list: []
    }
  },
  created() {
    this.getRoleList()
  },
  methods: {
    async getRoleList() {
      const { rows } = await getRoleList()
      console.log(rows)
      this.list = rows
    }
  }
}
</script>

<style scoped>
.role-operate {
  padding: 10px;
}
</style>
