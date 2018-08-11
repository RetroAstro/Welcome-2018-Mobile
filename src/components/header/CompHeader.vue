<template>
    <header class="header">
        <div class="nav">
            <ul class="btns-box flex-between animated bounceIn delay-1s">
                <li 
                v-for="(item, index) in items" 
                :key="index"
                :class="{active: item.name === currentName}" 
                class="btn bg-cover-all flex-center"
                :data-name="item.name"
                @click="handleSwitch(item)"
                >
                <span>{{item.name}}</span>
                </li>
            </ul>
        </div>
        <div class="robot-box bg-cover-all">
            <div class="hand bg-cover-all"></div>
            <div class="coin bg-cover-all"></div>
            <div class="coin-box bg-cover-all"></div>
            <div class="train bg-cover-all animated slower bounceIn delay-1s"></div>
            <div class="go bg-cover-all animated slower swing infinite delay-1s"></div>
            <div class="flag bg-cover-all"></div>
            <div class="right-pipe bg-cover-all"></div>
            <div class="left-pipe bg-cover-all"></div>
            <div class="countdown bg-cover-all">
                <div class="count-wrap">
                    <count-down></count-down>
                </div>
            </div>
        </div>
    </header>
</template>

<script>

import CountDown from './CountDown.vue'

export default {
  components: {
    CountDown
  },
  data () {
    return {
      currentName: '首页',
      items: [
        {
          name: '首页',
          path: 'index'
        },
        {
          name: '军训',
          path: 'training'
        },
        {
          name: '攻略',
          path: 'tips'
        },
        {
          name: '风采',
          path: 'mien'
        },
        {
          name: '活动',
          path: 'activity'
        }
      ],
      timeList: {
        day: [],
        hour: [],
        minute: [],
        second: []
      },
      timer: null
    }
  },
  methods: {
    handleSwitch (item) {
      this.currentName = item.name
      this.$router.push({path: `/${item.path}`})
    }
  }
}
</script>

<style lang="stylus" scoped>
.header {
    position relative
    width 100%
    height rem(245)
    .nav {
        position fixed
        top 0
        left 0
        width 100%
        height rem(50)
        background-color #9be9fe
        border-bottom 1.5px solid #33177b
        z-index 100
        .btns-box {
            margin 0 auto
            width 92%
            height rem(50)
            .btn {
                width rem(53)
                height rem(32)
                background-image url('../../assets/header_btn2.png')
                position relative
                & > span {
                    font-size rem(18)
                    color #fff
                    text-shadow rem(1.5) rem(1.5) #32167a
                    transform translate(rem(-3), rem(-3))
                }
            }
            .btn::after {
                visibility hidden
                display block
                content attr(data-name)
                position absolute
                top 0
                left 0
                right 0
                bottom 0
                background-image url('../../assets/header_btn1.png')
                background-size 100% 100%
                background-repeat no-repeat
                background-position center center
                z-index 200
                font-size rem(18)
                color #fff199
                text-shadow rem(1.5) rem(1.5) #32167a
                display flex
                align-items center
                justify-content center
                padding-right rem(6)
                padding-bottom rem(6)
            }
            .btn.active::after {
                visibility visible
            }
        }
    }
    .robot-box {
        position absolute
        top rem(50)
        left 0
        width 100%
        height rem(1100)
        background-image url('../../assets/banner.png')
        .hand {
            position absolute
            top rem(24)
            right rem(15)
            width rem(54)
            height rem(66)
            background-image url('../../assets/hand.png')
            z-index 6
        }
        .coin {
            position absolute
            top rem(85)
            right rem(30)
            width rem(28)
            height rem(23)
            background-image url('../../assets/coin.png')
            z-index 5
        }
        .coin-box {
            position absolute
            top rem(104)
            right rem(23)
            width rem(40)
            height rem(86)
            background-image url('../../assets/coin_box.png')
            z-index 4
        }
        .train {
            position absolute
            top rem(135)
            right rem(66)
            width rem(44)
            height rem(30)
            background-image url('../../assets/train.png')
        }
        .go {
            position absolute
            top rem(110)
            left rem(70)
            width rem(28)
            height rem(35)
            background-image url('../../assets/go.png')
        }
        .flag {
            position absolute
            top rem(142)
            left rem(86)
            width rem(33)
            height rem(31)
            background-image url('../../assets/flag.png')
        }
        .right-pipe {
            position absolute
            width rem(45)
            height rem(1670)
            top rem(260)
            right 0
            background-image url('../../assets/right_pipe.png')
            z-index 6
        }
        .left-pipe {
            position absolute
            width rem(20)
            height rem(1930)
            top rem(1100)
            left rem(8)
            background-image url('../../assets/left_pipe.png')
            z-index 6
        }
        .countdown {
            position absolute
            top rem(138)
            left rem(116)
            width rem(146)
            height rem(30)
            background-image url('../../assets/countdown.png')
            .count-wrap {
                width 86%
                height rem(30)
                margin 0 auto 
                position relative
            }
        }
    }
}
@media screen and (min-width: 540px) {
    .nav {
        width 540px !important
        position relative !important
        margin 0 auto
    }
}
</style>