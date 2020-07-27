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
      <!-- 修改箭头的颜色：除了默认的蓝色箭头外，Swiper还内置了白色   >     和黑色   >     两种箭头颜色，
      如需其他颜色可更改css样式中的007aff或使用其他图标。 -->
      <div class="swiper-button-prev swiper-button-white" slot="button-prev"></div>
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
        //---------网格分布 end-------------------------
        oberver: true, // 当改变swiper的样式（例如隐藏/显示）或者修改swiper的子元素时，自动初始化swiper。默认为false不更新。
        observeParents: true, //将observe应用于Swiper的父元素。当Swiper的父元素变化时，例如window.resize，Swiper更新。默认为false不更新。
        observeSlideChildren:true,  // 子slide更新时，swiper是否更新。默认为false不更新。

          //分页导航点设置
        pagination:{
          el: '.swiper-pagination',
          clickable : true, //设置为true时，可以通过点击控制跳转到对应的slide，否则只能显示当前slide位置
          type: 'bullets',
          bulletElement : 'li', //设定分页器指示器（小点）的HTML标签。
          dynamicBullets: true,  //动态分页器，当你的slide很多时，开启后，分页器小点的数量会部分隐藏。
          dynamicMainBullets: 2, //动态分页器的主指示点的数量
          hideOnClick: true, //默认分页器会一直显示。这个选项设置为true时点击Swiper会隐藏/显示分页器。
          },
          
          //前后导航设置
          //使用前进后退按钮来控制Swiper切换。
          // 有时你的按钮不想放在container之内，点击时可能会有蓝色的边框，加上样式outline: none 可以去除。
        navigation:{
            //设置前进按钮的css选择器或HTML元素。 
          nextEl:'.swiper-button-prev', // 类型是string，默认是null
           //
          prevEl: '.swiper-button-next', // 类型是string，默认是null

          //点击slide时显示/隐藏按钮。
            // BUG处理：如果遇到无效，可增加样式 .swiper-container .swiper-button-hidden{ opacity : 0; }
          hideOnClick: true
        },
        on:{
            //事件函数，navigation隐藏时执行。
             navigationHide: function(){
                alert('按钮隐藏了');
                },
                // 事件函数，navigation显示时执行。
                navigationShow: function(){
                    alert('按钮显示了');
                    }
        }


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

/* 修改左边导航样式 颜色 大小 和 位置 */
.swiper-button-prev{
    /* 修改颜色  只需要修改fill%3D'%23后面的六位颜色设置码9932cc*/
   background-image: url("data:image/svg+xml;charset=utf-8,%3Csvg%20xmlns%3D'http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg'%20viewBox%3D'0%200%2027%2044'%3E%3Cpath%20d%3D'M0%2C22L22%2C0l2.1%2C2.1L4.2%2C22l19.9%2C19.9L22%2C44L0%2C22L0%2C22L0%2C22z'%20fill%3D'%239932cc'%2F%3E%3C%2Fsvg%3E");
   /* 修改大小 */
   width: 6%;
   /* 修改背景大小 */
   background-size: contain;
   /* 修改位置 */
   left: 20px;
 }
 /* 修改右边导航样式 颜色 大小 和 位置 */
 .swiper-button-next{
   background-image: url("data:image/svg+xml;charset=utf-8,%3Csvg%20xmlns%3D'http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg'%20viewBox%3D'0%200%2027%2044'%3E%3Cpath%20d%3D'M27%2C22L27%2C22L5%2C44l-2.1-2.1L22.8%2C22L2.9%2C2.1L5%2C0L27%2C22L27%2C22z'%20fill%3D'%239932cc'%2F%3E%3C%2Fsvg%3E");
   width: 6%;
   background-size: contain;
   right: 20px;
 }
 /* 前进后退导航点击消失 Bug 修复 */
 .swiper-container .swiper-button-hidden{ opacity : 0; }
</style>