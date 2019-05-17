<template>
  <el-table
    :data="List"
    style="width: 100%"
    >
    <el-table-column
      prop="position"
      label="位置"
      width="180">
      <template slot-scope="scope">
        <span>{{scope.row.position}}</span>
      </template>
    </el-table-column>
    <el-table-column
      prop="x"
      label="横坐标 X"
      width="180">
      <template slot-scope="scope">
        <span>{{scope.row.x}}</span>
      </template>
    </el-table-column>
    <el-table-column
      prop="y"
      label="纵坐标 Y"
     >
      <template slot-scope="scope">
        <span>{{scope.row.y}}</span>
      </template>
    </el-table-column>
  </el-table>
</template>

<script>
export default {
  name: 'warn-table',
  data () {
    return {
      List: []
    }
  },
  mounted () {
    window.eventBus.$on('dot', (arg) => {
      var msg = {position: '最新位置', x: 0, y: 0}
      msg.x = arg.x
      msg.y = arg.y
      this.$set(this.List, 0, msg)
    })
  }
}
</script>

<style>
</style>
