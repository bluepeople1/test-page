<template>
    <div class="c-code">
        <vue-bstcode :text="text" :size="size" :logoSrc="logoSrc" :margin="margin"
                     :colorDark="colorDark" :colorLight="colorLight" :bgSrc="bgSrc"
                     :backgroundDimming="backgroundDimming" :logoScale="logoScale" :logoMargin="logoMargin"
                     :logoCornerRadius="logoCornerRadius" :whiteMargin="whiteMargin" :dotScale="dotScale"
                     :autoColor="autoColor" :binarize="binarize" :binarizeThreshold="binarizeThreshold"
                     :callback="callback" :correctLevel="correctLevel"></vue-bstcode>

    </div>
</template>

<script>
    import VueBstcode from 'vue-bstcode';

    export default {
        name: 'QRCode',
        props: {
            text: String || Number, // 编码内容
            size: Number, // 尺寸, 长宽一致, 包含外边
            logoSrc: String, // 二维码中心logo的地址
            margin: Number, // 二维码外边距,默认20px
            colorDark: String, // 二维码实点的颜色
            colorLight: String, // 空白区的颜色
            bgSrc: String, // 背景图地址
            backgroundDimming: String, // 叠加在背景图上的颜色
            logoScale: String, // 计算logo的大小 默认0.2f
            logoMargin: String, // logo周围的空白边框,默认为0
            logoCornerRadius: Number, // logo边框的圆角半径,默认为0
            whiteMargin: Boolean, // 背景图外的地方将绘制成白色边框,默认为true
            dotScale: String, // 数据区域点缩小比例,例:1.0f
            autoColor: Boolean, // 默认为true,背景图的主要颜色将作为实点的颜色
            binarize: Boolean, // 若为true,图像将被二进制处理,未指定则使用默认值,默认值为false
            binarizeThreshold: String, // 二值化处理的阈值
            callback: Function, // 生成二维码的data URI可以在回调中获取
            correctLevel: String // 错误率等级：L: 1、M: 0、Q: 3、H: 2，默认0
        },
        components: {
            VueBstcode
        }
    }
    ;
</script>
