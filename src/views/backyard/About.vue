<template>
  <div class="about">
    <div class="about-banner banner">
      <h1 class="banner-title">关于我</h1>
    </div>
    <!--中间内容-->
    <div  class="m-container m-about">
      <div class="ui container">

        <div class="ui stackable grid">
          <div class="eleven wide column">
            <div class="ui segment my-shadow">
              <img src="https://www.shuaigetu.net/uploads/img1/20200908/6dcac724c3fec9cfbcd8c63844daf07e.jpg" alt="" class="ui rounded image">
            </div>
          </div>
          <div class="five wide column">
            <div class="ui top attached segment my-shadow">
              <div class="ui header">关于我</div>
            </div>
            <div class="ui attached segment my-shadow">
              <p class="m-text">一个普通的java爱好者，对新奇的技术有着求知的欲望，但愿能与各位共同进步</p>
              <p class="m-text">热爱编程，喜欢仰望星空，希望此站能够记录我的学习心得</p>
            </div>
            <div class="ui attached segment my-shadow">
              <div class="ui orange basic left pointing label">编程</div>
              <div class="ui orange basic left pointing label">游泳</div>
              <div class="ui orange basic left pointing label">足球</div>
              <div class="ui orange basic left pointing label">运动</div>
            </div>
            <div class="ui attached segment my-shadow">
              <div class="ui my-blue basic left pointing label m-margin-tb-tiny">Java</div>
              <div class="ui my-blue basic left pointing label m-margin-tb-tiny">JavaScript</div>
              <div class="ui my-blue basic left pointing label m-margin-tb-tiny">Node</div>
              <div class="ui my-blue basic left pointing label m-margin-tb-tiny">ElasticSearch</div>
              <div class="ui my-blue basic left pointing label m-margin-tb-tiny">Web</div>
              <div class="ui my-blue basic left pointing label m-margin-tb-tiny">MySQL</div>
              <div class="ui my-blue basic left pointing label m-margin-tb-tiny">...</div>
            </div>
            <div class="ui bottom attached segment my-shadow">
              <a class="ui github circular icon button" data-content="https://gitee.com/fang-jiale" data-position="bottom center"><i class="github icon"></i></a>
              <a class="ui wechat circular icon button"><i class="weixin icon"></i></a>
              <a class="ui qq circular icon button" data-content="1109864130" data-position="bottom center"><i class="qq icon"></i></a>
            </div>

            <div class="ui wechat-qr flowing popup transition hidden">
              <img src="http://xrequest.cn/MrLiu.jpg" alt="" class="ui rounded image" style="width: 110px">
            </div>
          </div>
        </div>

      </div>
    </div>

    <div id="toolbar" class="m-padded m-fixed m-right-bottom" style="display: none">
      <div class="ui vertical icon buttons ">
        <button type="button" class="ui toc my-blue button" >目录</button>
        <a href="#comment-container" class="ui my-blue button" >留言</a>
        <button class="ui wechat icon button"><i class="weixin icon"></i></button>
        <div id="toTop-button" class="ui icon button" ><i class="chevron up icon"></i></div>
      </div>
    </div>

    <div class="ui toc-container flowing popup transition hidden" style="width: 250px!important;">
      <ol class="js-toc">

      </ol>
    </div>

    <div id="qrcode" class="ui wechat-qr flowing popup transition hidden " style="width: 130px !important;">
      <!--<img src="./static/images/wechat.jpg" alt="" class="ui rounded image" style="width: 120px !important;">-->
    </div>
    <br>
    <br>
  </div>

</template>

<script>

export default {
  data () {
    return {
      user: {},
      nickname: '',
      // 被激活的链接地址
      avatar: ''
    }
  },
  created () {
    this.getUser()
  },
  methods: {
    getUser () {
      this.user = window.sessionStorage.getItem('user')
      if (this.user != null) {
        this.nickname = JSON.parse(this.user).nickname
        this.avatar = JSON.parse(this.user).avatar
      }
    },
    logout () {
      window.sessionStorage.clear()
      this.$router.push('/home')
      // 刷新页面，删除vuex数据
      window.location.reload()
    }
  },
  mounted () {
    $('.menu.toggle').click(function () {
      $('.m-item').toggleClass('m-mobile-hide')
    })
    $('.ui.dropdown').dropdown({
      on: 'hover'
    })
    $('.wechat').popup({
      popup: $('.wechat-qr'),
      position: 'bottom center'
    })
    $('.qq').popup()
    $('.github').popup()
  }
}
</script>

<style scoped>
 .about-banner {
   height: 480px;
   background: url(https://r.photo.store.qq.com/psc?/V53KcXfb1umonn4HbITu3rINxs43TczD/45NBuzDIW489QBoVep5mcQz6a6RmGKe6G3ZOYoIoQdl9VNaSpHgiv8JNMAcpsS2xpNxouAuqFxY8uNvPxZ3qr6E798TSOFY*de6Bx*vCMlY!/r) center
   center / cover no-repeat;
   background-color: #49b1f5;}
 .container{
   animation: main 1.0s;
 }
 .m-about {
   padding-top: 450px !important;
   padding-bottom: 0 !important;
 }
</style>
