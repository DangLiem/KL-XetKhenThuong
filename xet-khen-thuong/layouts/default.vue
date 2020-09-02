<template>
  <v-app>
    <v-navigation-drawer
      v-model="drawer"
      :mini-variant="miniVariant"
      :clipped="true"
      fixed
      app
      color="indigo lighten-5"
    >
      <v-list>
        <v-list-item
          v-for="(item, i) in items"
          :key="i"
          :to="item.to"
          router
          exact
        >
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title v-text="item.title" />
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar dark :clipped-left="clipped" fixed app color="#253b7f">
      <v-btn icon @click.stop="miniVariant = !miniVariant">
        <v-icon>mdi-{{ `chevron-${miniVariant ? 'right' : 'left'}` }}</v-icon>
      </v-btn>
      <v-toolbar-side-icon>
        <v-img :src="require('@/assets/img/logo.png')" width="50" height="50" />
      </v-toolbar-side-icon>
      <v-toolbar-title class="px-3" v-text="title" />
      <v-text-field
        flat
        solo-inverted
        hide-details
        prepend-inner-icon="mdi-magnify"
        label="Tìm kiếm thông tin danh hiệu sinh viên"
        class="hidden-sm-and-down pl-10"
      ></v-text-field>
      <v-spacer></v-spacer>
    </v-app-bar>
    <v-main>
      <v-container>
        <nuxt />
      </v-container>
    </v-main>
    <v-footer dark app color="#253b7f" class="">
      <div class="footer">
        <span
          >&copy; {{ new Date().getFullYear() }} Trường Đại học Công nghệ, Đại
          học Quốc Gia Hà Nội</span
        >
      </div>
    </v-footer>
  </v-app>
</template>
<style scoped>
.footer {
  font-size: 12px;
}
</style>
<script>
export default {
  data() {
    return {
      clipped: true,
      drawer: false,
      fixed: false,
      items: [
        {
          icon: 'mdi-apps',
          title: 'Dashboard',
          to: '/',
        },
        {
          icon: 'mdi-chart-bubble',
          title: 'Đánh giá danh hiệu',
          to: '/inspire',
        },
        {
          icon: 'mdi-chart-bubble',
          title: 'Thống kê danh hiệu',
          to: '/inspire',
        },
      ],
      miniVariant: false,
      right: true,
      title: 'Xét Khen Thưởng',
    }
  },
}
</script>
