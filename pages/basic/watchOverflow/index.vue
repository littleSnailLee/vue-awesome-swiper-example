<template>
  <div>
    <!-- 轮播图开始 -->
    <div class="swiper-container" v-swiper:MySwiper="swiperOption"  >
      <div class="swiper-wrapper">
        <div class="swiper-slide" v-for="banner in banners" :key="banner.id">
            <img :src="banner.imageUrl">
        </div>
      </div>
      <!-- <div class="swiper-scrollbar" slot="scrollbar"></div> -->
      <div class="swiper-pagination swiper-pagination-black " slot="pagination" ></div>
      <div class="swiper-button-prev swiper-button-black" slot="button-prev"></div>
      <div class="swiper-button-next swiper-button-black" slot="button-next"></div>
    </div>
    <!-- 轮播图结束 -->

    <ul>
      <li>
          <h2> <a href='/'>返回首页</a> </h2>
      </li>
      <li>
          <h2> <a href='/basic'>一般选项</a> </h2>
      </li>
      <li>
          <h2><a href='/basic/parallax'>视差效果图</a></h2>
      </li>
      <li>
          <h2> <a href='/basic/virtualTranslate'>虚拟移动</a></h2>
      </li>
      <li>
          <h2><a href='/basic/autoHeight'>自动高度</a></h2>
      </li>
      <li>
          <h2><a href='/basic/runCallbacksOnInit'>初始化回调函数</a></h2>
      </li>
      <li>
          <h2><a href='/basic/watchOverflow'>一张图片显示</a></h2>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data(){
    return {
      banners:[
        {id:1,imageUrl:'/images/1.jpg'},
      ],
      swiperOption:{
        //  -------------------一般选项start--------------------
        // 初始化slide索引，默认初始化是显示第一张slide，如果想要显示其他slide，可以设置此项
        initialSlide: 1, //类型是number，0是第一张，以此类推

         //设置轮播图的滑动方向，可设置为水平方向切换（horizontal) 或 垂直方向切换（vertical)
         // ps: 垂直方向切换时需要在swiper-container上设置高度
        direction: 'horizontal', //类型是String，默认是horizontal

         //设置slide切换时的速度，也就是slide开始切换到结束的时间（单位是ms),也是移动端触摸释放时，滑动到贴合的时间
        speed: 900, //类型是数字 默认是300，
         
         //鼠标移动到录播图中的形状设置，设置为true时，鼠标移动到录播图中指针变为手掌形状，拖动时指针变成抓手形状
        grabCursor: true, //类型是 Boolean 默认false

          //视觉效果设置parallax ,可以设置slide进出透明度或者缩放，进入时，由透明或者缩小到正常不透明显示，出去时，有正常不透明到缩小透明
          // 详见/parallax，

          //设置包装wrapper的大小，Swiper使用flexbox布局(display: flex)，开启这个设定会在Wrapper上添加等于slides相加的宽或高，在对flexbox布局的支持不是很好的浏览器中可能需要用到。
        setWrapperSize: true, //类型是Boolean ，默认值是false

         // virtualTranslate 设置虚拟位移，虚拟导航点、progress可以看到slide切换变化，但是页面只显示第一张slide，详见/virturalTranslate

         //roundLengths 设置大约长度，如果设置为true，则将slide的宽和高取整(四舍五入)，以防止某些分辨率的屏幕上文字或边界(border)模糊。
         // 例如当你设定slidesPerView : 3时，则可能出现slide的宽度为341.33px，开启roundLengths后宽度取整数341px。
        roundLengths: true, //类型是Boolean， 默认是false

         // breakpoints ----> todo <-----

         // autoHeight 设置图片自动高度，container和wrapper高度随着slide高度变化而变化，详见/autoHeight

         // runCallbacksOnInit: 如果你的初始化slide不是第一个(例initialSlide:2)或者设置了loop: true，那么初始化时会触发一次 [Transition/SlideChange] [Start/End] 回调函数。 详见/runCallbacksOnInit

         // watchOverflow  当没有足够的slide切换时，例如只有1个slide，swiper会失效且隐藏导航等。默认不开启这个功能。
        watchOverflow: true, //类型是Boolean，默认是false
          //分页导航点设置
        pagination:{
          el: '.swiper-pagination',
          clickable : true, //设置为true时，可以通过点击控制跳转到对应的slide，否则只能显示当前slide位置
          type: 'bullets',
          // type: 'fraction', // 样式：1/4 2/4 3/4 4/4
          // type : 'progressbar', // 进度条
          // type : 'custom', //自定义
          progressbarOpposite: false, //使进度条分页器与Swiper的direction参数相反 
          bulletElement : 'span', //设定分页器指示器（小点）的HTML标签。
          dynamicBullets: true,  //动态分页器，当你的slide很多时，开启后，分页器小点的数量会部分隐藏。
          dynamicMainBullets: 2, //动态分页器的主指示点的数量
          hideOnClick: true, //默认分页器会一直显示。这个选项设置为true时点击Swiper会隐藏/显示分页器。
          },
          //前后导航设置
        navigation:{
          nextEl:'.swiper-button-prev',
          prevEl: '.swiper-button-next',
          // hideOnClick: true
        },


      }
    }
  }
}
</script>
<style>
  .swiper-container{
    background-image:url(/background/parallax.jpg);
    background-repeat: no-repeat;
    background-size: cover;
    height: 600px;
  }
  .swiper-wrapper{
    text-align: center;
  }
   /* 修改导航小圆点 大小 背景色 */
  .swiper-pagination-bullet {
      /* 设置导航点圆点 */
   width:16px ;
   height:16px ;
   /* 设置背景色 */
   background-color: rgb(231, 10, 10);
   /* 设置透明度 */
   opacity: .6;
   /* 设置元素堆叠顺序，将导航点设置到最上面 */
   z-index: 100;
 }
 /* 修改导航小圆点间距 */
 .swiper-container-horizontal > .swiper-pagination-bullets .swiper-pagination-bullet{
   margin: 0 10px;
 }
</style>