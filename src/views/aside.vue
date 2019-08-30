<template>
  <div style="width:300px">
    <el-menu
      default-active="2"
      class="el-menu-vertical-demo"
      @open="handleOpen"
      @close="handleClose">
      <el-submenu index="1">
        <template slot="title">
          <i class="el-icon-location"></i>
          <span>导航一</span>
        </template>
        <el-menu-item-group>
          <template slot="title">分组一</template>
          <el-menu-item index="1-1">选项1</el-menu-item>
          <el-menu-item index="1-2">选项2</el-menu-item>
        </el-menu-item-group>
        <el-menu-item-group title="分组2">
          <el-menu-item index="1-3">选项3</el-menu-item>
        </el-menu-item-group>
        <el-submenu index="1-4">
          <template slot="title">选项4</template>
          <el-menu-item index="1-4-1">选项1</el-menu-item>
        </el-submenu>
      </el-submenu>
      <el-menu-item index="2">
        <i class="el-icon-menu"></i>
        <span slot="title">导航二</span>
      </el-menu-item>
      <el-menu-item index="3" disabled>
        <i class="el-icon-document"></i>
        <span slot="title">导航三</span>
      </el-menu-item>
      <el-menu-item index="4">
        <i class="el-icon-setting"></i>
        <span slot="title">导航四</span>
      </el-menu-item>
    </el-menu>
    <el-menu
      class="el-menu-headBar"
      <!--侧边栏的方向 水平 -->
      mode="horizontal"
      @select="handleSelect"
      background-color="#000000"
      text-color="#fff"
      active-text-color="#ffd04b"
      :unique-opened="true"
      :default-active="onRoutes" router>
      <template v-for="item in items" >
        <template v-if="item.subs" >
          <el-submenu  :index="item.index">
            <template slot="title" >
             {{item.title}}
            </template>
            <el-menu-item v-for="(subItem,i) in item.subs" :key="i" :index="subItem.index">
              {{ subItem.title }}
            </el-menu-item>
          </el-submenu>
        </template>
        <template v-else>
          <el-menu-item :index="item.index">
            <label>{{ item.title }}</label>
          </el-menu-item>
        </template>
      </template>
    </el-menu>
  </div>
</template>

<script>
export default {
  data(){
    return {
       activeIndex: "1",
        items: [
          {
            icon: 'el-icon-menu',
            index: '1',
            title: '数据统计',
            subs: [
              {
                index: '/monitor',
                title: '客流展示'
              },
              {
                index: '/monitor/device',
                title: '设备采集'
              },
              {
                index: '/monitor/tv',
                title: '监控视频'
              }
            ]
          },{
            icon: 'el-icon-goods',
            index: '/product',
            title: '商品管理',
          },{
            icon: 'el-icon-goods',
            index: '/category',
            title: '类目管理',
          },{
            icon: 'fa  fa-cart-arrow-down',
            index: '/order',
            title: '订单一览'
          },{
            icon: 'fa fa-user-o',
            index: '/merchant',
            title: '商家信息'
          },{
            icon: 'el-icon-printer',
            index: '9',
            title: '微商城',
            subs:[
              {
                icon: 'el-icon-printer',
                index: '/banner',
                title: 'banner设置'
              },{
                icon: 'el-icon-printer',
                index: '/decoration',
                title: '首页装修'
              },{
                icon: 'el-icon-printer',
                index: '/message',
                title: '消息设置'
              }
            ]
          },{
            icon: 'el-icon-printer',
            index: '10',
            title: '线下店',
            subs:[
              {
                icon: 'el-icon-printer',
                index: '/device',
                title: '设备管理'
              },{
                icon: 'el-icon-printer',
                index: '/advertise',
                title: '广告管理'
              },{
                icon: 'el-icon-printer',
                index: '/version',
                title: '版本管理'
              }
            ]
          },{
            icon: 'el-icon-printer',
            index: '/largeUI',
            title: '大屏'
          },{
            icon: 'el-icon-printer',
            index: '/coupon',
            title: '优惠券'
          }
        ],
    }
  },
  methods:{

  }
}
</script>