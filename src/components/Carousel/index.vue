<template>
    <div class="swiper-container" id="floor1Swiper" ref="cur">
        <div class="swiper-wrapper">
            <div class="swiper-slide" v-for="img in list" :key="img.id">
                <img :src="img.imgUrl">
            </div>
        </div>
        <!-- 如果需要分页器 -->
        <div class="swiper-pagination"></div>

        <!-- 如果需要导航按钮 -->
        <div class="swiper-button-prev"></div>
        <div class="swiper-button-next"></div>
    </div>
</template>

<script>
    import Swiper from 'swiper';
    export default {
        name: 'Carousel',
        props: ['list'],
        watch: {
            list: {
                immediate: true,
                handler() {
                    this.$nextTick(() => {
                        //这个回调执行后，保证数据已经回来了。
                        var mySwiper = new Swiper(this.$refs.cur, {
                            // direction: 'vertical', // 垂直切换选项
                            loop: true, // 循环模式选项
                            clickable: true,
                            // 如果需要分页器
                            pagination: {
                                el: '.swiper-pagination',
                            },
                            // 如果需要前进后退按钮
                            navigation: {
                                nextEl: '.swiper-button-next',
                                prevEl: '.swiper-button-prev',
                            },
                        })
                    })
                }
            }
        }
    }
</script>

<style>

</style>