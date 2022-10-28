<template>
  <div class="about">
    <a href="">
      <el-card class="category"><i class="el-icon-folder-opened"></i>&nbsp;&nbsp;&nbsp;&nbsp;JavaMVC相关</el-card>
    </a>
    <a href="">
      <el-card class="article"><i class="el-icon-tickets"></i>&nbsp;&nbsp;&nbsp;&nbsp;JavaMVC原理</el-card>
    </a>
    <div id="roo">
      <el-row id="row">
        <el-button type="primary" round>首页</el-button>
        <el-button type="success" round>新建</el-button>
        <el-button type="info" round>社区</el-button>
      </el-row>
    </div>
  </div>
</template>

<style>
.category{
  background-color: #dad669;
  display: inline-block;
  width: 200px;
  height: 60px;
  margin-right: 10px;
}
.article{
  background-color: #eae4f3;
  display: inline-block;
  width: 200px;
  height: 60px;
  margin-right: 10px;
}
#row{
  display: inline-block;
  margin: 0 auto;
}
#roo{
  position: fixed;
  text-align: center;
  left: 0;
  right: 0;
  bottom: 100px;
}
</style>
