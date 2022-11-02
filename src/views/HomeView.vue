<template>
  <div class="home">
    <el-container>
      <el-header class="layout-header"><h1 style="line-height: 60px">小白云notebook</h1></el-header>
        <el-main class="layout-main">
          <el-card style="height:100%;overflow-y:auto;overflow-x:hidden;" id="cart">
            <router-view/>
          </el-card></el-main>
      <el-footer class="layout-footer">
        <div class="col s12 m8 l8 copy-right" style="margin-top: 10px">
          Copyright&nbsp;©
          <span id="year">2022-现在</span>
          |邮箱：2276780432@qq.com
          |Welcome to 小白云notebook
          <br>
          <span id="busuanzi_container_site_pv" style="display: inline;">
                &nbsp;<i class="far fa-eye"></i>&nbsp;<a href="https://beian.miit.gov.cn" style="text-decoration: none">鲁ICP备2022032659号</a>&nbsp;
            </span>
          <span id="busuanzi_container_site_uv" style="display: inline;">
                |&nbsp;<i class="fas fa-users"></i>&nbsp;暂时搁置&nbsp;
            </span>
          <br>
          <br>
        </div>
      </el-footer>
    </el-container>
  </div>
</template>

<script>

</script>
<style>
.home{
  height: 100%;
}
.el-card__body{
  height: 100%;
}
card{
  position: relative;
  display: inline-block;
}
.layout-header {
  background: #89da64;
}
.layout-footer{
  position: fixed;
  background-color: rgba(190, 195, 199, 0.38);
  bottom: 0;
  height: 70px !important;
  left: 0;
  right: 0;
  text-align: center;
}
.layout-main {
  position: absolute;
  top: 60px;
  bottom: 70px;
  left: 0;
  right: 0;
}
</style>