<template>
  <v-navigation-drawer
    v-model="toggle"
    fixed app>
    <v-toolbar flat dark :color="$root.themeColor" class="toolbar">
      <router-link :to="{ name: 'Dashboard' }">
        <img src="static/logo.png" width="36px"></img>
      </router-link>
      <router-link :to="{ name: 'Dashboard' }" class="text">
         Gradius
      </router-link>
    </v-toolbar>
    <v-list>
      <v-list-tile @click="changeRoute('Dashboard', 1)">
        <v-list-tile-action>
          <v-icon>dashboard</v-icon>
        </v-list-tile-action>
        <v-list-tile-title :class="[{'active': selectedIndex === 1}, 'item-title' ]" >หน้าหลัก</v-list-tile-title>
      </v-list-tile>

      <v-list-group
        prepend-icon="person">
        <v-list-tile slot="activator">
          <v-list-tile-title class="item-title">ผู้ใช้งาน</v-list-tile-title>
        </v-list-tile>
        <v-list-tile @click="changeRoute('radcheck', 2)">
          <v-list-tile-action>
            <v-icon>person</v-icon>
          </v-list-tile-action>
          <v-list-tile-title :class="[{'active': selectedIndex === 2}, 'item-title' ]">ชื่อผู้ใช้งาน</v-list-tile-title>
        </v-list-tile>
        <v-list-tile @click="changeRoute('Chart', 5)">
          <v-list-tile-action>
            <v-icon>group</v-icon>
          </v-list-tile-action>
          <v-list-tile-title :class="[{'active': selectedIndex === 5}, 'item-title' ]">กลุ่มผู้ใช้งาน</v-list-tile-title>
        </v-list-tile>
        <v-list-tile @click="changeRoute('Media', 6)">
          <v-list-tile-action>
            <v-icon>fas fa-tasks</v-icon>
          </v-list-tile-action>
          <v-list-tile-title :class="[{'active': selectedIndex === 6}, 'item-title' ]">จัดการ Attribute</v-list-tile-title>
        </v-list-tile>
        <v-list-tile @click="changeRoute('Snackbar', 1)">
          <v-list-tile-action>
            <v-icon>fas fa-signal</v-icon>
          </v-list-tile-action>
          <v-list-tile-title :class="[{'active': selectedIndex === 7}, 'item-title' ]">รายงานสถานะผู้ใช้</v-list-tile-title>
        </v-list-tile>
    </v-list-group>

      <v-list-group
        prepend-icon="event_note">
        <v-list-tile slot="activator">
          <v-list-tile-title class="item-title">ผู้ดูแลระบบ</v-list-tile-title>
        </v-list-tile>
        <v-list-tile @click="changeRoute('Snackbar', 7)">
          <v-list-tile-action>
            <v-icon>fas fa-database</v-icon>
          </v-list-tile-action>
          <v-list-tile-title :class="[{'active': selectedIndex === 7}, 'item-title' ]">Database Backup</v-list-tile-title>
        </v-list-tile>
        <v-list-tile @click="changeRoute('Snackbar', 1)">
          <v-list-tile-action>
            <v-icon>far fa-file-excel</v-icon>
          </v-list-tile-action>
          <v-list-tile-title :class="[{'active': selectedIndex === 7}, 'item-title' ]">Excel Loader</v-list-tile-title>
        </v-list-tile>
        <v-list-tile @click="changeRoute('Snackbar', 7)">
          <v-list-tile-action>
            <v-icon>fas fa-history</v-icon>
          </v-list-tile-action>
          <v-list-tile-title :class="[{'active': selectedIndex === 7}, 'item-title' ]">Logs</v-list-tile-title>
        </v-list-tile>
      </v-list-group>

      <v-list-group
        prepend-icon="build">
        <v-list-tile slot="activator">
          <v-list-tile-title class="item-title">ตั้งค่า</v-list-tile-title>
        </v-list-tile>
        <v-list-tile @click="changeRoute('Snackbar', 7)">
          <v-list-tile-action>
            <v-icon>settings</v-icon>
          </v-list-tile-action>
          <v-list-tile-title :class="[{'active': selectedIndex === 7}, 'item-title' ]">RADIUS SERVER</v-list-tile-title>
        </v-list-tile>
      <v-list-tile @click="changeRoute('Snackbar', 7)">
        <v-list-tile-action>
          <v-icon>settings</v-icon>
        </v-list-tile-action>
        <v-list-tile-title :class="[{'active': selectedIndex === 7}, 'item-title' ]">RADIUS CLIENT</v-list-tile-title>
      </v-list-tile>
      </v-list-group>
<!--        <v-list-tile @click="$router.push({ name: 'Error', params: { errorCode: '403' } })">-->
<!--          <v-list-tile-action>-->
<!--            <v-icon>cancel</v-icon>-->
<!--          </v-list-tile-action>-->
<!--          <v-list-tile-title class="item-title">403</v-list-tile-title>-->
<!--        </v-list-tile>-->

<!--        <v-list-tile @click="$router.push({ name: 'Error', params: { errorCode: '404' } })">-->
<!--          <v-list-tile-action>-->
<!--            <v-icon>cancel</v-icon>-->
<!--          </v-list-tile-action>-->
<!--          <v-list-tile-title class="item-title">404</v-list-tile-title>-->
<!--        </v-list-tile>-->

<!--        <v-list-tile @click="$router.push({ name: 'Error', params: { errorCode: '500' } })">-->
<!--          <v-list-tile-action>-->
<!--            <v-icon>cancel</v-icon>-->
<!--          </v-list-tile-action>-->
<!--          <v-list-tile-title class="item-title">500</v-list-tile-title>-->
<!--        </v-list-tile>-->

<!--        <v-list-tile @click="$router.push({ name: 'Login' })">-->
<!--          <v-list-tile-action>-->
<!--            <v-icon>cancel</v-icon>-->
<!--          </v-list-tile-action>-->
<!--          <v-list-tile-title class="item-title">Login</v-list-tile-title>-->
<!--        </v-list-tile>-->
    </v-list-group>
    </v-list>
  </v-navigation-drawer>
</template>

<script>
export default {
  props: {
    toggle: {
        type: Boolean,
        required: false,
        default: true
    }
  },

  data() {
    return {
      selectedIndex: 1
    }
  },

  methods: {
    changeRoute(routeName, selectedIndex) {
      const vm = this;

      vm.selectedIndex = selectedIndex;

      return vm.$router.push({ name: routeName });
    }
  }
}
</script>

<style>
  .toolbar {
    font-weight: bold;
    font-size: 18px;
  }

  .toolbar .text {
    padding-left: 15px;
    color: white;
    text-decoration:none;
  }

  .item-title {
    font-size: 17px;
    font-weight: 500;
  }
  .item-sub-title {
    font-size: 15px;
    font-weight: 500;
  }

  .active {
    font-weight: bold;
  }
</style>
