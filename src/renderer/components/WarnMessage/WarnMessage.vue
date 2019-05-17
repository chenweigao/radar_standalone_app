<template>
  <el-table 
  :data="contents"
  style="width: 100%"
  :default-sort = "{prop: 'time', order: 'descending'}"
  stripe class="animated bounceInUp">
    <el-table-column 
    label="时间"
    prop="time"
    sortable
    >
      <template slot-scope="scope">
        <span>{{scope.row.time}}</span>
      </template>
    </el-table-column>
    <el-table-column
    prop="position" 
    label="位置">
      <template slot-scope="scope">
        <span>{{scope.row.position}}</span>
      </template>
    </el-table-column>
    <el-table-column
    prop="message" 
    label="事件">
      <template slot-scope="scope">
        <span>{{scope.row.message}}</span>
      </template>
    </el-table-column>
  </el-table>
</template>
<script>
export default {
  name: 'warn-message',
  data () {
    return {
      contents: []
    }
  },
  methods: {
  },
  mounted () {
    window.eventBus.$on('warnning', (event) => {
      console.log(event)
      this.contents.push(event)
    })
  }
}
</script>

<style>

</style>