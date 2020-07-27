<template>
  <div>
    <!-- 轮播图开始 -->
    <div class="swiper-container " v-swiper:MySwiper="swiperOption">
        <div class="swiper-wrapper" >
           
            <div class="swiper-slide" v-for="banner in banners" :key="banner.id" >
                <!-- <img :src="banner.imageUrl" data-swiper-parallax-x="-600" data-swiper-parallax-opacity="0.2"> -->
                <img :src="banner.imageUrl" 
                data-swiper-parallax="0" 
                data-swiper-parallax-scale="0.5" 
                data-swiper-parallax-opacity="0.5" 
                data-swiper-parallax-duration=3000>
            </div>
        </div>
      <!-- <div class="swiper-scrollbar" slot="scrollbar"></div> -->
      <div class="swiper-pagination swiper-pagination-black "  slot="pagination" ></div>
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
        {id:2,imageUrl:'/images/2.jpg'},
        {id:3,imageUrl:'/images/3.jpg'},
        {id:4,imageUrl:'/images/4.jpg'},
        {id:5,imageUrl:'/images/5.jpg'},
        {id:6,imageUrl:'/images/6.jpg'},
      ],
      swiperOption:{
        //  -------------------一般选项start--------------------
        // 初始化slide索引，默认初始化是显示第一张slide，如果想要显示其他slide，可以设置此项
        initialSlide: 0, //类型是number，0是第一张，以此类推

         //设置轮播图的滑动方向，可设置为水平方向切换（horizontal) 或 垂直方向切换（vertical)
         // ps: 垂直方向切换时需要在swiper-container上设置高度
        direction: 'horizontal', //类型是String，默认是horizontal

         //设置slide切换时的速度，也就是slide开始切换到结束的时间（单位是ms),也是移动端触摸释放时，滑动到贴合的时间
        speed: 1200, //类型是数字 默认是300，
         
         //鼠标移动到录播图中的形状设置，设置为true时，鼠标移动到录播图中指针变为手掌形状，拖动时指针变成抓手形状
        grabCursor: true, //类型是 Boolean 默认false
         /**
          * 轮播图的视差效果：
          * 如果设置为true，开启轮播图的视觉效果，slide在切换过程中显得有层次感
          * 此效果可以应用到container或者slide的子元素上面，当应用于container的子元素时，常用于视差在背景图上
          * 1. 视差位移变化
          *     在所需要的元素上增加data-swiper-parallax属性（与Swiper切换方向相同）或data-swiper-parallax-x（x方向）data-swiper-parallax-y（y方向）
          *     data-swiper-parallax接受两种类型的参数:
          *         number（单位：px），如-300，从右边300px进入左边出去。
          *         percentage（百分比），移动距离=该元素宽度 * percentage。
          * 2. 视差透明度变化
          *     在所需要的元素上增加data-swiper-parallax-opacity属性。可选值0-1，如0.5，从半透明进入半透明出去
          * 3.视差缩放变化
          *     在所需要的元素上增加data-swiper-parallax-scale属性。可选值如0.5，从一半大小进入一半大小出去
          * 还可通过data-swiper-parallax-duration设定视差动画持续时间（ms）。默认值是Swiper的speed，与切换时间同步。
          * 设定透明度或缩放必须同时设定位移，否则无效
          *      <div data-swiper-parallax="0" data-swiper-parallax-opacity="0.5" >透明度变化</div>
          * 
          * 
          */
         parallax: true, //类型是Boolean 默认是false
         
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
    background-image: url(/background/parallax.jpg);
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