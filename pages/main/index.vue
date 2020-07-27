<template>
  <div>
    <!-- 轮播图开始 -->
    <!-- v-if 是为了异步请求获取数据之前，不渲染轮播图，只有获取数据后再渲染 -->
    <div class="swiper-container" v-swiper="swiperOption" v-if="banners.length>0" >
      <div class="swiper-wrapper">
        <div class="swiper-slide" v-for="banner in banners" :key="banner.id">
            <img :src="banner.imageUrl" 
            data-swiper-parallax-opacity=0.5 
            data-swiper-parallax-scale=0.5 >
        </div>
      </div>
      <div class="swiper-scrollbar" slot="scrollbar"></div>
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
                initialSlide: 1, //初始化显示第二张轮播图，默认是0
                 //设置轮播图的滑动方向，可设置为水平方向切换（horizontal) 或 垂直方向切换（vertical)
                 // ps: 垂直方向切换时需要在swiper-container上设置高度
                direction: 'horizontal',  //slide水平切换方向
                speed: 1000,  //设置slide切换时的速度，也就是slide开始切换到结束的时间（单位是ms)，默认是300，
                grabCursor: true,  //设置鼠标移动到录播图中的形状，设置为true时，鼠标移动到录播图中指针变为手掌形状，拖动时指针变成抓手形状
                parallax: true, //开启轮播图的视觉效果，slide在切换过程中显得有层次感，在所需要的元素上增加data-swiper-parallax-opacity/scale属性,可选值0-1
                // autoHeight: true, //设置为true时，随着slide高度的变化，swiper的container和wrapper高度随之变化，否则高度会按照slide最大高度显示
                watchOverflow:true, //只有1个slide，swiper会失效且隐藏导航等。默认不开启这个功能。(loop模式下无效)
                slidesPerView:3, //每页显示三张slide
                centeredSlides: true, //一个页面显示多个slide时，active 激活的slide会居中显示，而不是默认情况下的左边
                // slidesPerGroup:3, // 一组有多少张slide，页面切换时一次切换一组，而不是一张（carousel 模式下），不能与centeredSlides同用
                // spaceBetween : 20, //在slide之间设置距离（单位px）。
                oberver: true, // 当改变swiper的样式（例如隐藏/显示）或者修改swiper的子元素时，自动初始化swiper。默认为false不更新。
                observeParents: true, //将observe应用于Swiper的父元素。当Swiper的父元素变化时，例如window.resize，Swiper更新。默认为false不更新。
                observeSlideChildren:true,  // 子slide更新时，swiper是否更新。默认为false不更新。
                loop: true, //开启loop模式,会在原本slide前后复制若干个slide(默认一个)并在合适的时候切换，让Swiper看起来是循环的。
                autoplay:{ //启动自动切换，并使用默认的切换设置。
                    delay: 1000, // 1s 切换一次
                    stopOnLastSlide: false, // 设置为true，当切换到最后一个slide时停止自动切换。（loop模式下无效）。
                    disableOnInteraction:false, // 禁止互动 ,用户操作swiper之后自动切换不会停止，操作包括触碰(touch)，拖动，点击pagination等
                    reverseDirection:false, // 开启反向自动轮播
                    waitForTransition: true,//默认情况下，自动切换会在slide过渡完毕后才开始计时。关闭等待过渡时间，上一张slide开始切换时，计时开始，delay时间到立刻3切换
                },
                /**
                 * effect slide的切换效果，默认为"slide"（位移切换）
                 * 可设置为'slide'（普通切换、默认）,"fade"（淡入）"cube"（方块）"coverflow"（3d流）"flip"（3d翻转）。
                 */
                effect:'slide',
                // effect:'fade', // 淡入淡出
                //  fadeEffect:{ 
                //     crossFade:true, //开启淡出。过渡时，原slide透明度从1->0（淡出），过渡中的slide透明度从0->1（淡入），其他slide透明度0。
                // },
                // 开启cube，需关闭slidesPerView和缩放效果，同时将container大小设置为图片大小
                // effect: 'cube',
                // cubeEffect:{
                //     slideShadows: true,   // 开启slide阴影。默认 true。
                //     shadow: true,        //开启投影。默认 true。
                //     shadowOffset: 100,   //投影距离。默认 20，单位px。
                //     shadowScale: 0.8     //投影缩放比例。默认0.94。
                // },
                // effect: 'coverflow', //coverflow 需要配合slidesPerView、centeredSlides使用
                // coverflowEffect: {
                //     rotate: 30,           // slide做3d旋转时Y轴的旋转角度,默认是50
                //     stretch: 20,          //每个slide之间的拉伸值，越大slide靠得越紧。5.3.6 后可使用%百分比,默认是0
                //     depth: 100,           //slide的位置深度。值越大z轴距离越远，看起来越小。默认是100
                //     modifier: 2,          // depth和rotate和stretch的倍率，相当于depth*modifier、rotate*modifier、stretch*modifier，值越大这三个参数的效果越明显。默认是1
                //     slideShadows : true   //是否开启slide阴影
                // },
                // effect: 'flip',
                // flipEffect: {
                //     slideShadows : true, //slides的阴影。默认true。
                //     limitRotation : true, //限制最大旋转角度为180度，默认true。
                // },
                 //使用分页器导航。分页器可使用小圆点样式（默认）、分式样式或进度条样式。
                pagination:{
                el: '.swiper-pagination', //分页器容器的css选择器或HTML标签。分页器等组件可以置于container之外.
                clickable : true, //设置为true时，点击分页器的指示点分页器会控制Swiper切换，否则只能显示当前slide位置
                type: 'bullets',
                 /**
                 * 分页器样式类型，可选
                 * ‘bullets’  圆点（默认）
                 * ‘fraction’  分式  样式：1/4 2/4 3/4 4/4
                 * ‘progressbar’  进度条
                 * ‘custom’ 自定义
                 */
                //   type: 'progressbar',
                //   progressbarOpposite: true, // 使进度条分页器与Swiper的direction参数相反 
                bulletElement : 'span', //设定分页器指示器（小点）的HTML标签。
                dynamicBullets: true,  //动态分页器，当你的slide很多时，开启后，分页器小点的数量会部分隐藏。
                dynamicMainBullets: 2, //动态分页器的主指示点的数量
                hideOnClick: true, //默认分页器会一直显示。这个选项设置为true时点击Swiper会隐藏/显示分页器。
                },
                //前后导航设置
                navigation:{
                nextEl:'.swiper-button-prev', //设置前进按钮的css选择器或HTML元素。 
                prevEl: '.swiper-button-next',
                // hideOnClick: true //点击slide时隐藏按钮。
                },
                //为Swiper增加滚动条。
                scrollbar:{
                    el: '.swiper-scrollbar', //Scrollbar容器的css选择器或HTML元素。
                    hide: false, // 滚动条是否自动隐藏。默认：false，不会自动隐藏。 swiper不滚动的情况下，自动隐藏。
                    draggable:true, //该参数设置为true时允许拖动滚动条。为了方便拖动，设置css,高度设置10px
                    snapOnRelease: false, //如果设置为false，释放滚动条时slide不会自动贴合。
                    dragSize:200, // 设置滚动条指示的尺寸。默认'auto': 自动，或者设置num(单位是px)。
                },
                keyboard: {   
                    enabled: true, //开启键盘上下按键切换
                    onlyInViewport: true, //默认仅控制当前窗口内的swiper切换。当swiper离开可视区域则无法切换。禁止后，即使swiper不在可视区域也能键盘控制切换
                },
                mousewheel:{
                    releaseOnEdges:true, // 如果开启这个参数，当Swiper处于边缘位置时（第一个或最后一个slide），Swiper释放鼠标滚轮事件，鼠标可以控制页面滚动。
                    invert:true,  // 这个参数会使鼠标滚轮控制方向反转
                },
                 zoom:{
                    maxRatio:4, // 设置缩放的最大放大比例。，默认是3
                    minRatio:1, // 最小缩放焦距（缩小倍率）。默认是1
                    toggle:true,// 是否允许双击缩放。设置为false，不允许双击缩放，只允许手机端触摸缩放。
                },
                // 事件注册
                on: {
                    slideChangeTransitionEnd: function(){
                    alert(this.activeIndex);//切换结束时，告诉我现在是第几个slide
                    },
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
    /* 切换效果为cube时，开启该选项 */
    /* width: 600px;   */
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