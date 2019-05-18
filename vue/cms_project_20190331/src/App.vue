<template>
  <div id="app">
    <!--<img src="./assets/logo.png">-->
    <!--<router-view/>-->
    <el-tabs v-model="activeName" type="card" @tab-click="handleClick">
      <el-tab-pane label="列表" name="first"><table-comp/></el-tab-pane>
      <el-tab-pane label="表单" name="second"><form-comp/></el-tab-pane>

    </el-tabs>
  </div>
</template>
<script>
import tableComp from '@/components/tableComp'
import formComp from '@/components/formComp'
export default {
  components: {
    tableComp: tableComp,
    formComp: formComp
  },
  data () {
    return {
      activeName: 'first'
    }
  },
  methods: {
    handleClick (tab, event) {
      // console.log(tab, event)
    }
  }
}
</script>

<style>

</style>
