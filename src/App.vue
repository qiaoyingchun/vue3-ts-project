<template>
  <div class="container">
    <global-header :user="user"></global-header>
    <column-list :list="list"></column-list>
  </div>
</template>
<script lang="ts">
import { defineComponent } from 'vue'
import 'bootstrap/dist/css/bootstrap.min.css'
import ColumnList, { ColumnProps } from '@/components/ColumnList.vue'
import GlobalHeader, { UserProps } from './components/GlobalHeader.vue'
const currentUser: UserProps = {
  isLogin: true,
  name: '张三'
}
const testData: ColumnProps[] = [
  {
    id: 1,
    title: 'test1栏',
    description: '的飞机发动机股份接口的',
    avatar: 'https://t10.baidu.com/it/u=2696207298,454295397&fm=58'
  },
  {
    id: 2,
    title: 'test1栏',
    description: '的飞机发动机股份接口的',
    avatar: 'https://t10.baidu.com/it/u=2696207298,454295397&fm=58'
  },
  {
    id: 3,
    title: 'test1栏',
    description: '的飞机发动机股份接口的'
    // avatar: 'https://t10.baidu.com/it/u=2696207298,454295397&fm=58'
  },
  {
    id: 4,
    title: 'test1栏',
    description: '的飞机发动机股份接口的',
    avatar: 'https://t10.baidu.com/it/u=2696207298,454295397&fm=58'
  }
]
export default defineComponent({
  name: 'App',
  components: {
    ColumnList,
    GlobalHeader
  },
  setup () {
    return {
      list: testData,
      user: currentUser
    }
  }
})
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
