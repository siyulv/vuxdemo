<!-- 资讯 -->
<template>
  <div>
    <!-- 轮播图 -->
    <swiper :list="imgs" auto style="width:50%;height:120px;margin:0 auto;" dots-class="custom-bottom" dots-position="center"></swiper>
  </div>
</template>

<script>
    // 引入 vux 内部组件
    import { Swiper } from 'vux'
    // 引入 api接口文档
    // import { getList } from '../../api'

    // 轮播图列表
    const imgList = [
        'https://cdn.pixabay.com/photo/2018/07/14/15/27/cafe-3537801__480.jpg',
        'https://cdn.pixabay.com/photo/2019/03/30/21/03/space-4092053__480.jpg',
        'https://cdn.pixabay.com/photo/2015/05/29/19/17/study-789631__480.jpg',
        'https://cdn.pixabay.com/photo/2017/08/06/22/19/house-2596975__480.jpg',
        'http://file06.16sucai.com/2016/0315/1df566087c24a94cd9534bc9bc1871ff.jpg'
    ];

    // 轮播图图片地址列表
    const urlList = imgList.map((one, index) => ({
        url: 'javascript:',  //这里填写图片点击的链接
        img: one
    }));

    export default {
        name: 'NewsList',
        components:{
            Swiper
        },
        data(){
            return {
                imgs:urlList,
            }
        }
    }
</script>
