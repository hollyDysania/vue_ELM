<template>
  <div id='header' >
     <div class="content-wra">
         <div class="avatar">
             <img width="64" height="64" :src="seller.avatar">
         </div>
         <div class="content">
             <div class="title">
                 <span class="brand"></span>
                 <span class="name">{{seller.name}}</span>
             </div>
            <div class="decs">
                {{seller.description}}/{{seller.deliveryTime}}分钟送达
            </div>
            <div v-if="seller.supports" class="supports">
                <span class="icon" :class="classMap[seller.supports[0].type]"></span>
                <span class="text">{{seller.supports[0].description}}</span>
            </div>
         </div>
         <div v-if="seller.supports" class="support-count">
             <div class="count">{{seller.supports.length}}个
                 <i class="icon-keyboard_arrow_right"></i>
             </div>
         </div>
     </div>
     <div class="bulletin-wra">
         <span class="bulletin-title"></span>
         <span class="bulletin-text">{{seller.bulletin}}</span>
         <i class="icon-keyboard_arrow_right"></i>
     </div>
     <div class="background">
         <img :src="seller.avatar" width="100%" height="100%">
     </div>
     <div class="detail"></div>
  </div>
</template>
<script type="text/ecmascript-6">
export default {
  name: "header",
  props:['seller'],
  created(){
      this.classMap = ['decrease','discount','spacial','invoice','guarantee']
  },
  data () {
    return {
    };
  }
}
</script>
<style lang="stylus"  rel="stylesheet/stylus">
@import '../../../common/stylus/mixin.styl';
#header
    position relative
    color:#fff
    overflow hidden
    background-color rgba(7,17,27,0.5)
    .content-wra
        padding:24px 12px 18px 24px
        font-size:0
        position :relative
        .avatar
            display:inline-block
            vertical-align :top
            img 
                border-radius :4px
        .content
            display:inline-block    
            margin-left:16px
            .title
                 margin 2px 0 8px 0
                .brand
                    display:inline-block
                    vertical-align :top
                    width:30px
                    height:18px
                    bg-image('brand')
                    background-size :30px 18px
                    background-repeat :no-repeat
                .name 
                    margin-left:6px
                    font-size:16px
                    line-height :18px
                    font-weight bold

            .decs
                margin-bottom :10px
                line-height :12px
                font-size :12px
                color:rgba(255,255,255,0.8)
            .supports
                .icon
                    display: inline-block
                    width :12px
                    height :12px
                    margin-right :4px
                    background-size :12px 12px
                    background-repeat :no-repeat
                    vertical-align :top
                    &.decrease
                        bg-image('decrease_1')
                    &.discount
                        bg-image('discount_1')
                    &.guarantee
                        bg-image('guarantee_1')
                    &.invoice
                        bg-image('invoice_1')
                    &.spacial
                        bg-image('special_1') 
                 .text
                    line-height :12px
                    font-size :10px
                    color:rgba(255,255,255,0.8)
                       
        .support-count
            position :absolute
            bottom:14px
            right :12px
            padding :0 8px
            height :24px
            line-height :24px
            border-radius :14px
            background:rgba(0,0,0,0.2)
            text-align :center
            color:rgba(255,255,255,0.8)
            .count
                font-size :10px
                vertical-align :top
            .icon-keyboard_arrow_right
                font-size :10px
    .bulletin-wra
        position relative
        height 28px
        line-height 28px
        padding 0 22px 0 12px
        background-color rgba(0,0,0,0.2)
        white-space nowrap 
        overflow hidden
        text-overflow  ellipsis
        .bulletin-title
            display inline-block
            height 12px
            width 22px
            bg-image('bulletin')
            background-size 22px 12px
            background-repeat no-repeat
            vertical-align middle
        .bulletin-text
           color:rgba(255,255,255,0.8)
           font-size 12px 
        .icon-keyboard_arrow_right
            position absolute
            font-size 10px
            right 12px
            top 8px
            line-height 18px
    .background
        position absolute
        top 0
        left 0
        width 100%
        height 100%
        z-index -1
        filter blur(10px)

</style>