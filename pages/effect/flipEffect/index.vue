<template>
<div>
    <!-- 轮播图开始 -->
    <div class="swiper-container" v-swiper:MySwiper="swiperOption"  >
    <div class="swiper-wrapper">
        <div class="swiper-slide" v-for="banner in banners" :key="banner.id">
            <img :src="banner.imageUrl"  >
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
        <h2> <a href='/effect/fadeEffect'>淡入淡出效果</a> </h2>
    </li>
    <li>
        <h2> <a href='/effect/cubeEffect'>立方体效果</a> </h2>
    </li>
    <li>
        <h2> <a href='/effect/coverflow'>旋转Overflow</a> </h2>
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
        initialSlide: 5, // 初始化 显示第6个slide，默认第一张，0 是第一个，以此类推
        direction: 'horizontal', //slide切换方向 水平
        speed: 900, //类型是数字 默认是300，
        grabCursor: true, //鼠标进入到swiper，显示手掌形状，拖动显示抓手
        //------------------------一般选项 end------------------------
        oberver: true, // 当改变swiper的样式（例如隐藏/显示）或者修改swiper的子元素时，自动初始化swiper。默认为false不更新。
        observeParents: true, //将observe应用于Swiper的父元素。当Swiper的父元素变化时，例如window.resize，Swiper更新。默认为false不更新。
        observeSlideChildren:true,  // 子slide更新时，swiper是否更新。默认为false不更新。
        loop:true,//开启循环，播放完最后一张，从第一张开始
        //autoplay 设置为true启动自动切换，并使用默认的切换设置。
        autoplay:{
            delay: 1000, // 自动切换的时间间隔 1s 切换一次
            stopOnLastSlide: true, // 如果设置为true，当切换到最后一个slide时停止自动切换。（loop模式下无效）
            disableOnInteraction:false, // /用户操作swiper之后，autoplay停止， 设置为false，操作也不停止
            reverseDirection:true, // 开启反向自动轮播。
            waitForTransition: false,//默认为true，等待过渡完毕。自动切换会在slide过渡完毕后才开始计时。设置为false，过渡开始时就开始计时
        },

        // effect slide的切换效果，默认为"slide"（位移切换），
        // 可设置为'slide'（普通切换、默认）,"fade"（淡入）"cube"（方块）"coverflow"（3d流）"flip"（3d翻转）。
        // effect: 'slide', // 类型是String，默认是slide

        effect: 'flip',
        /**
         * flipEffect
         * 3d翻转有两个参数可设置。
         *  slideShadows：slides的阴影。默认true。
         *  limitRotation：限制最大旋转角度为180度，默认true。
         */
             flipEffect: {
                slideShadows : true,
                limitRotation : true,
            },
            centeredSlides:true,
            centeredSlidesBound:true,
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
    width: 600px;
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