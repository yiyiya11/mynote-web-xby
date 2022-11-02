<template>
  <div class="index">
    <a href="" v-for="type in Types">
      <el-card class="category"><i class="el-icon-folder-opened"></i>&nbsp;&nbsp;&nbsp;&nbsp;{{type.typename}}</el-card>
    </a>
    <a href="">
      <el-card class="article"><i class="el-icon-tickets"></i>&nbsp;&nbsp;&nbsp;&nbsp;JavaMVC原理</el-card>
    </a>
    <div id="buttons">
      <el-row id="row">
        <el-button type="primary" @click="indext" round>首页</el-button>
        <el-button type="success" @click="newAddTyoe" round>新建类别</el-button>
        <el-button type="info" @click="newAddArticle" round>新建文章</el-button>
        <el-button type="warning" round>社区</el-button>
      </el-row>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      parend:{
        typeId:0,
        userId:1
      },
      Types:[],
      Type:{
        userId:"",
        typename:"",
        parendId:"",
      }
    }
  },
  methods: {
    indext(){
      location.reload()
    },
    newAddArticle(){
      location.href="/NewArticle?"+this.parend.userId+"/"+this.parend.typeId;
    },
    listType(parentId){
      let url="http://localhost:8090/Type/listByParendId"
      this.axios.get(url+"?parentId="+parentId+"&userId="+this.parend.userId).then((response=>{
        console.log(response)
        let responseBydy=response.data;
        this.Types=responseBydy.data;
      }))
    },
    newAddTyoe(){
      this.$prompt('请输入分类名', '提示', {
        confirmButtonText: '确定',
        cancelButtonText: '取消',
      }).then(({ value }) => {
        this.Type.typename=value;
        this.Type.userId=this.parend.userId;
        this.Type.parendId=this.parend.typeId;
        let url="http://localhost:8090/Type/addNew"
        let qs=this.qs.stringify(this.Type)
        this.axios.post(url,qs).then((response)=>{
          let responsebody=response.data.state
          responsebody==20000?(
              this.$message.success("添加类别成功"),
              this.listType(this.parend.typeId)
          ):this.$message.warning("添加类别失败");
        })
      }).catch(() => {
        this.$message({
          type: 'info',
          message: '取消输入'
        });
      });
    }
    },
    created() {
      this.listType(0)
    }

}
</script>

<style>
#buttons{
  text-align: center;
}
#row{
  display: inline-block;
}
.index{
  height: 100%;
}
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
#buttons{
  position: fixed;
  bottom: 100px;
  right: 0;
  left: 0;
}
</style>
