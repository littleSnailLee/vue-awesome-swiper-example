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
          <h2> <a href='/grid'>网格分布</a> </h2>
      </li>
      <li>
          <h2> <a href='/basic'>一般选项</a> </h2>
      </li>
      <li>
          <h2><a href='/grid/slidesPerView'>每页多个slide</a></h2>
      </li>
      <li>
          <h2> <a href='/grid/centeredSlides'>active slide 居中</a></h2>
      </li>
      <li>
          <h2><a href='/grid/slidesPerGroup'>分组显示</a></h2>
      </li>
      <li>
          <h2><a href='/grid/slidesPerGroupSkip'>slide跳过分组</a></h2>
      </li>
      <li>
          <h2><a href='/grid/slidesOffset'>前后位移量</a></h2>
      </li>
      <li>
          <h2><a href='/grid/centerInsufficientSlides'>slide 小于 perView</a></h2>
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
        {id:6,imageUrl:'/images/6.jpg'}
      ],
      swiperOption:{
        //  -------------------一般选项start--------------------
          initialSlide: 1, // 初始化 显示第2个slide，默认第一张，0 是第一个，以此类推
          direction: 'horizontal', //slide切换方向 水平
          speed: 900, //类型是数字 默认是300，
          grabCursor: true, //鼠标进入到swiper，显示手掌形状，拖动显示抓手
          roundLengths: true, //slide大约宽度
        //------------------------一般选项 end------------------------

        //-----------------网格分布 start----------------------
         /**
          * slidesPerView 设置slider容器能够同时显示的slides数量(carousel模式)。
          * 可以设置为数字（可为小数，小数不可loop），或者 'auto'则自动根据slides的宽度来设定数量
          * loop模式下如果设置为'auto'还需要设置另外一个参数loopedSlides。
          * slidesPerView: 'auto'目前还不支持多行模式（当slidesPerColumn > 1）
          */
        // slidesPerView:2,// 类型是数字或者‘auto' ， 默认值是1
        slidesPerView:2,
        // slidesPerView: 'auto',


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