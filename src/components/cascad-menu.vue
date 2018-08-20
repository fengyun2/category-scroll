<template>
  <div class="cascad-menu" ref="cascadMenu">
    <scroll class="left-menu" :data="menus" ref="leftMenu">
      <div class="left-menu-container">
        <ul>
          <li class="left-item" ref="leftItem" :class="{'current': currentIndex === index}" @click="selectLeft(index, $event)" v-for="(menu, index) in menus" :key="index">
            <p class="text">{{menu.name}}</p>
          </li>
        </ul>
      </div>
    </scroll>
    <scroll class="right-menu" :data="menus" ref="rightMenu" @scroll="scrollHeight" :listenScroll="true" :probeType="3">
      <div class="right-menu-container">
        <ul>
          <li class="right-item" ref="rightItem" v-for="(menu, index) in menus" :key="index">
            <div class="title">{{menu.name}}</div>
            <ul>
              <li v-for="(item, j) in menu.data" :key="j">
                <div class="data-wrapper">
                  <div class="data">{{item.name}}</div>
                </div>
              </li>
            </ul>
          </li>
        </ul>
      </div>
    </scroll>
  </div>
</template>

<script>
import Scroll from './scroll'
export default {
  components: {
    Scroll
  },
  props: {
    menus: {
      required: true,
      type: Array,
      default: () => []
    }
  },
  data () {
    return {
      rightTops: [],
      scrollY: 0,
      leftScrollY: 0
    }
  },
  computed: {
    currentIndex () {
      // 当用户在滚动时，需要计算当前滚动距离在哪个(右边li块)区间内，并拿到它的 `index`
      const { scrollY, rightTops } = this
      console.log('scrollY: ', scrollY)
      console.log('rightTops: ', rightTops)

      let index = rightTops.findIndex((height, index) => {
        return scrollY >= rightTops[index] && scrollY < rightTops[index + 1]
      })
      if (scrollY > rightTops[index] + 50) {
        index++
      }
      console.log('currentIndex: ', index)

      return index
    }
  },
  mounted () {
    this.$nextTick(() => {
      this._calculateHeight()
    })
  },
  methods: {
    selectLeft (index, event) {
      // 添加`$event`是为了区分原生点击事件还是 better-scroll派发的事件
      console.log('selectLeft - index: ', index)
      if (!event._constructed) {
        return
      }
      let rightItem = this.$refs.rightItem
      let el = rightItem[index]
      this.$refs.rightMenu.scrollToElement(el, 300)
    },
    scrollHeight (pos) {
      // console.log('scrollHeight - pos: ', pos)
      this.scrollY = Math.abs(Math.round(pos.y))
    },
    _calculateHeight () {
      // 计算右边列表每一块的高度
      let lis = this.$refs.rightItem
      let height = 0
      this.rightTops.push(height)
      Array.from(lis).forEach(li => {
        height += li.clientHeight
        this.rightTops.push(height)
      })
    }
  }
}
</script>

<style lang="stylus" scoped>
.cascad-menu {
  display: flex;
  position: absolute;
  top: 100px;
  bottom: 100px;
  width: 100%;
  border: 1px solid red;
  overflow: hidden;

  .left-menu {
    flex: 0 0 80px;
    width: 80px;
    background: #f3f5f7;

    .left-item {
      height: 54px;
      width: 100%;
      margin-left: -20px;

      &.current {
        width: 200%;
        margin-left: -40px;
        background: #fff;
      }

      .text {
        width: 100%;
        line-height: 54px;
      }
    }
  }

  .right-menu {
    flex: 1;

    .right-item {
      height: 100%;
      margin-left: -40px;
      border: 1px solid #ccc;

      .title {
        border-bottom: 1px solid #ccc;
        height: 20px;
      }

      .data-wrapper {
        .data {
          line-height: 40px;
          height: 40px;
          margin-left: -40px;
        }
      }
    }
  }
}
</style>
