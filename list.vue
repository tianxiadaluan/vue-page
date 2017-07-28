<template>
  <div>
    <pagination :pageNum='p' :perRows='pagesize' :totalCount='totalCount' :listname="listname"></pagination>
  </div>
</template>
<script>
  //引入分页模块
  import pagination from './pagination'
  export default {
    data () {
      return {
        pagesize: 1, //单页显示条数
        p: 1, //当前页
        totalCount:100, //总条数
        listname:'',  //分页路由的name值
      }
    },
    components:{
      pagination
    }
</script>
