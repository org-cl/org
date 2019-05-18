<template>
  <div>
    <el-table
      ref="singleTable"
      :data="tableData"
      style="width: 100%"
      border
      @selection-change="rowChange"
      >
      <!--row-class-name="rowClassName"-->
      <!-- 单选 -->
      <!--highlight-current-row-->
      <!--@current-change="rowChange"-->
      <el-table-column v-for="item in columnList"
        :type="item.type"
        :fixed="item.fixed"
        :prop="item.prop"
        :sortable="item.sortable"
        :label="item.label"
        :width="item.width"
        :align="item.align">
      </el-table-column>
      <el-table-column label="操作" width="240px">
        <template slot-scope="scope">
          <el-button size="mini" type="primary" @click="handleEdit(scope.$index, scope.row)" icon="el-icon-edit"></el-button>
          <el-button size="mini" type="primary" @click="handleDelete(scope.$index, scope.row)" icon="el-icon-delete"></el-button>
          <el-button size="mini" type="primary" @click="handleDelete(scope.$index, scope.row)" icon="el-icon-view"></el-button>
        </template>
        <!--<template slot-scope="scope">-->
          <!--<el-button @click="handleClick(scope.row)" type="text" size="small">查看</el-button>-->
          <!--<el-button type="text" size="small">编辑</el-button>-->
        <!--</template>-->
      </el-table-column>
    </el-table>
    <div style="margin-top: 20px">
      <!--<el-button @click="setCurrent(tableData[1])">选中行</el-button>-->
      <!--<el-button @click="setCurrent()">取消选择</el-button>-->
      <el-button @click="toggleSelection([tableData[2], tableData[3]])">多选</el-button>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      tableData: [
        {date: '2015-05-12', name: '张三', province: '上海', city: '浦东新区', address: '张扬路 1518 弄', zip: '210210'},
        {date: '2016-06-12', name: '李四', province: '湖北', city: '武汉', address: '青山区民族大道路 1518 号', zip: '422563'},
        {date: '2017-07-12', name: '王五', province: '上海', city: '浦东新区', address: '张扬路 1528 弄', zip: '210210'},
        {date: '2018-08-12', name: '周六', province: '上海', city: '浦东新区', address: '张扬路 418 弄', zip: '210210'},
        {date: '2019-09-12', name: '赵七', province: '上海', city: '浦东新区', address: '张扬路 658 弄', zip: '210210'},
        {date: '2014-10-12', name: '王八', province: '上海', city: '浦东新区', address: '张扬路 18 弄', zip: '210210'}
      ],
      columnList: [
        {type: 'selection', width: 'fixed', align: 'center'},
        {type: 'index', fixed: true, label: '序号', width: '200px', align: 'center'},
        {prop: 'date', label: '日期', width: '200px', align: 'center'},
        {prop: 'name', label: '姓名', width: '400px', align: 'center', sortable: true},
        {prop: 'province', label: '省份', width: '400px', align: 'center'},
        {prop: 'city', label: '市区', width: '400px', align: 'center'},
        {prop: 'address', label: '详细地址', width: '400px', align: 'center'},
        {prop: 'zip', label: '邮编', width: '400px', align: 'center'}
      ],
      fixed: true
    }
  },
  methods: {
    rowClassName (row, index) {
      if (row === null) {
        return ''
      } else if (index % 2 === 0) {
        return 'success-row'
      } else {
        return 'warning-row'
      }
    },
    rowChange (row, index) {
      console.log(row)
      console.log(index)
      this.currentRow = row
    },
    setCurrent (row) {
      this.$refs.singleTable.setCurrentRow(row)
    },
    // 多选
    toggleSelection (rows) {
      if (rows) {
        rows.forEach(row => {
          this.$refs.singleTable.toggleRowSelection(row)
        })
      } else {
        this.$refs.singleTable.clearSelection()
      }
    },
    handleEdit (index, row) {
      console.log(index, row)
    },
    handleDelete (index, row) {
      console.log(index, row)
    }
  }
}
</script>

<style scoped>
  .el-table .warning-row {
    background: oldlace;
  }

  .el-table .success-row {
    background: #f0f9eb;
  }
</style>
