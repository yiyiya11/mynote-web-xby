<template>
  <div class="about">
    <p v-html="markdown"></p>
  </div>
</template>
<script>
import MarkDowdIt from 'markdown-it';

export default {
  data(){
    return {
      content:'### 1.2 函数式编程思想\n' +
          '\n' +
          '#### 1.2.1 概念\n' +
          '\n' +
          '​\t面向对象思想需要关注用什么对象完成什么事情。而函数式编程思想就类似于我们数学中的函数。它主要关注的是对数据进行了什么操作。\n' +
          '\n' +
          '#### 1.2.2 优点\n' +
          '\n' +
          '* 代码简洁，开发快速\n' +
          '* 接近自然语言，易于理解\n' +
          '* 易于"并发编程"'
    }
  },
  computed:{
    markdown(){
      const md=new MarkDowdIt();
      const retult=md.render(this.content)
      return retult
    }
  }
}
</script>