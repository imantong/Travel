<template>
  <div class="icons">
    <swiper :options="swiperOption">
      <swiper-slide v-for="(page, index) of pages" :key="index">
        <div 
          class="icon" 
          v-for="item of page"
          :key="item.id"
        >
          <div class="icon-img">
            <img class="icon-img-content" :src="item.imgUrl" />
          </div>
          <p class="icon-desc">{{item.desc}}</p>
        </div>
      </swiper-slide>
    </swiper>
  </div>
</template>

<script>
  export default {
    name: 'HomeIcon',
    data () {
      return {
        swiperOption: {
          autoplay: false
        },
        iconList: [{
          id: '001',
          imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/95/f3dd6c383aeb3b02.png',
          desc: '景点门票'
        }, {
          id: '002',
          imgUrl: 'http://img1.qunarzz.com/piao/fusion/1804/5a/13ceb38dcf262f02.png',
          desc: '一日游'
        }, {
          id: '003',
          imgUrl: 'http://img1.qunarzz.com/piao/fusion/1804/ff/fdf170ee89594b02.png',
          desc: '杭州必游'
        }, {
          id: '004',
          imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/75/eca3ce656c886502.png',
          desc: '漂流'
        }, {
          id: '005',
          imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/6a/45f595250c73d102.png',
          desc: '夏日玩水'
        }, {
          id: '006',
          imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/17/99402a22ce4af302.png',
          desc: '西湖'
        }, {
          id: '007',
          imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/e3/67df61427c8e1302.png',
          desc: '宋城千古情'
        }, {
          id: '008',
          imgUrl: 'http://img1.qunarzz.com/piao/fusion/1804/95/8d02011d149bdb02.png',
          desc: '汽车票'
        }, {
          id: '009',
          imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/75/eca3ce656c886502.png',
          desc: '千岛湖'
        }, {
          id: '010',
          imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/80/416c6ab3368d1f02.png',
          desc: '全部玩乐'
        }]
      }
    },
    computed: {
      pages () {
        const pages = []
        this.iconList.forEach((item, index) => {
          const page = Math.floor(index / 8)
          if (!pages[page]) {
            pages[page] = []
          }
          pages[page].push(item)
        })
        return pages
      }
    }
  }
</script>

<style lang="stylus" scoped>
  @import '~styles/varibles.styl'
  @import '~styles/mixins.styl'
  .icons >>> .swiper-container
    height: 0
    padding-bottom: 50%
  .icons
    margin-top: .1rem
    .icon
      position: relative
      width: 25%
      float: left
      overflow: hidden
      height: 0
      padding-bottom: 25%
      .icon-img
        position: absolute
        top: 0
        left: 0
        right: 0
        bottom: .44rem
        box-sizing: border-box
        padding: .1rem
        .icon-img-content
          display: block
          margin: 0 auto
          height: 100%
      .icon-desc
        position: absolute
        left: 0
        right: 0
        bottom: 0
        height: .44rem
        line-height: .44rem
        text-align: center
        color: $darkTextColor
        ellipsis()
</style>