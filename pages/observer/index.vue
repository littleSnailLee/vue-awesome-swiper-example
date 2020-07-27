<template>
  <div>
    <!-- 轮播图开始 -->
    <div class="swiper-container" v-swiper:MySwiper="swiperOption"  >
      <div class="swiper-wrapper">
        <div class="swiper-slide" v-for="banner in banners" :key="banner.id">
            <img :src="banner.imageUrl" data-swiper-parallax-opacity=0.5
         data-swiper-parallax-scale=0.5 >
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
          parallax: true,// 视觉效果 进入和出去设置为透明度0.5，缩放0.5
        //------------------------一般选项 end------------------------

        //-----------------网格分布 start----------------------
        slidesPerView:3,// 类型是数字或者‘auto' ， 默认值是1
        centeredSlides: true, //active 居中显示，默认是左边
        //---------网格 分布 end-------------------------

         //启动动态检查器(OB/观众/观看者)，当改变swiper的样式（例如隐藏/显示）或者修改swiper的子元素时，自动初始化swiper。
         // 默认false，不开启，可以使用update()方法更新。
        oberver: true, // 类型是Boolean 默认是false

         // 将observe应用于Swiper的父元素。当Swiper的父元素变化时，例如window.resize，Swiper更新。
        observeParents: true, //// 类型是Boolean 默认是false

         // 子slide更新时，swiper是否更新。默认为false不更新。
        observeSlideChildren:true,  // 类型是Boolean 默认是false


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