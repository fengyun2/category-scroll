<template>
  <div id="app">
    <cascad-menu :menus="menus"></cascad-menu>
  </div>
</template>

<script>
import CascadMenu from './components/cascad-menu.vue'
export default {
  name: 'app',
  components: {
    CascadMenu
  },
  data () {
    return {
      menus: [
        {
          name: '菜单1',
          data: [
            {
              name: '1.1'
            },
            {
              name: '1.2'
            },
            {
              name: '1.3'
            },
            {
              name: '1.4'
            },
            {
              name: '1.5'
            },
            {
              name: '1.6'
            }
          ]
        },
        {
          name: '菜单8',
          data: [
            {
              name: '1.1'
            },
            {
              name: '1.2'
            },
            {
              name: '1.3'
            },
            {
              name: '1.4'
            },
            {
              name: '1.5'
            },
            {
              name: '1.6'
            }
          ]
        },
        {
          name: '菜单2',
          data: [
            {
              name: '1.1'
            },
            {
              name: '1.2'
            },
            {
              name: '1.3'
            },
            {
              name: '1.4'
            },
            {
              name: '1.5'
            },
            {
              name: '1.6'
            }
          ]
        },
        {
          name: '菜单3',
          data: [
            {
              name: '1.1'
            },
            {
              name: '1.2'
            },
            {
              name: '1.3'
            },
            {
              name: '1.4'
            },
            {
              name: '1.5'
            },
            {
              name: '1.6'
            }
          ]
        },
        {
          name: '菜单4',
          data: [
            {
              name: '1.1'
            },
            {
              name: '1.2'
            },
            {
              name: '1.3'
            },
            {
              name: '1.4'
            },
            {
              name: '1.5'
            },
            {
              name: '1.6'
            }
          ]
        },
        {
          name: '菜单5',
          data: [
            {
              name: '1.1'
            },
            {
              name: '1.2'
            },
            {
              name: '1.3'
            },
            {
              name: '1.4'
            },
            {
              name: '1.5'
            },
            {
              name: '1.6'
            }
          ]
        },
        {
          name: '菜单6',
          data: [
            {
              name: '1.1'
            },
            {
              name: '1.2'
            },
            {
              name: '1.3'
            },
            {
              name: '1.4'
            },
            {
              name: '1.5'
            },
            {
              name: '1.6'
            }
          ]
        },
        {
          name: '菜单7',
          data: [
            {
              name: '1.1'
            },
            {
              name: '1.2'
            },
            {
              name: '1.3'
            },
            {
              name: '1.4'
            },
            {
              name: '1.5'
            },
            {
              name: '1.6'
            }
          ]
        },
        {
          name: '菜单8',
          data: [
            {
              name: '1.1'
            },
            {
              name: '1.2'
            },
            {
              name: '1.3'
            },
            {
              name: '1.4'
            },
            {
              name: '1.5'
            },
            {
              name: '1.6'
            }
          ]
        },
        {
          name: '菜单9',
          data: [
            {
              name: '1.1'
            },
            {
              name: '1.2'
            },
            {
              name: '1.3'
            },
            {
              name: '1.4'
            },
            {
              name: '1.5'
            },
            {
              name: '1.6'
            }
          ]
        }
      ],
      translatedText: '',
      list: [],
      pullup: true
    }
  }
}
</script>
<style lang="stylus">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

li {
  list-style: none;
  heigh: 60px;
}
</style>
