<template>
  <div>
    <el-breadcrumb separator="/">
      <el-breadcrumb-item><a href="/index">首页</a></el-breadcrumb-item>
      <el-breadcrumb-item>发表文章</el-breadcrumb-item>
    </el-breadcrumb>


    <mavon-editor v-model="content" ref="md" @change="change" style="min-height: 470px" />
    <br>
    <b>是否公开该文章:</b>&nbsp;&nbsp;&nbsp;
    <el-radio-group v-model="radio">
      <el-radio :label="0"><b>公开</b></el-radio>
      <el-radio :label="1"><b>私有</b></el-radio>
    </el-radio-group>
    <el-button id="button" @click="NewArticle" type="primary">发布文章</el-button>
  </div>
</template>

<style>
button{
  position: relative;
  left: 950px;
}
</style>
<script>
// 导入组件 及 组件样式
import { mavonEditor } from 'mavon-editor'
import 'mavon-editor/dist/css/index.css'
export default {
  components: {
    mavonEditor
  },
  // content:输入的markdown
  // html：及时转的html
  data () {
    return {
      parent:{
        userId:'',
        typeId:''
      },
      article:{
        title:'',
        userId:'',
        content:'',
        classId:'',
        isPublic:''
      },
      radio: 0,
      content: '',
      html: ''
    }
  },
  methods: {
    NewArticle(){
      let url='http://localhost:8090/';
      this.axios.post(url,)
    },
    // 所有操作都会被解析重新渲染
    change (value, render) {
      // render 为 markdown 解析后的结果[html]
      this.html = render
    },
    // 提交
    submit () {
      console.log(this.content)
      console.log(this.html)
    }
  },
  mounted () {
    let parentxx=location.search
    parentxx=parentxx.split("?");
    parentxx=parentxx[1].split("%2F");
    this.parent.userId=parentxx[0];
    this.parent.typeId=parentxx[1];
  }
}
</script>