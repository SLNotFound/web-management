<template>
  <div class="container">
    <div class="app-container">
      <el-tree default-expand-all :data="depts" :props="defaultProps" />
    </div>
  </div>
</template>

<script>
export default {
  name: 'Department',
  data() {
    return {
      depts: [{
        name: '天下第一',
        children: [
          { name: '总经办' },
          { name: '行政中心' },
          { name: '财务部' }
        ]
      }],
      defaultProps: {
        label: 'name',
        children: 'children'
      }
    }
  }
}
</script>

<style scoped>
.app-container {
  padding: 30px 140px;
  font-size: 14px;
}
</style>
