<template>
  <v-app>
    <v-navigation-drawer
      v-model="drawer"
      :clipped="$vuetify.breakpoint.lgAndUp"
      app
      color="indigo lighten-5"
      width="280"
    >
      <v-list dense>
        <template v-for="item in items">
          <v-list-group v-if="item.children" :key="item.title">
            <template v-slot:activator>
              <v-list-item-action>
                <v-icon>{{ item.icon }}</v-icon>
              </v-list-item-action>
              <v-list-item-content>
                <v-list-item-title>
                  {{ item.title }}
                </v-list-item-title>
              </v-list-item-content>
            </template>
            <v-list-item
              v-for="(child, i) in item.children"
              :key="i"
              :to="child.to"
            >
              <v-list-item-action>
                <v-icon>{{ child.icon }}</v-icon>
              </v-list-item-action>
              <v-list-item-content>
                <v-list-item-title>
                  {{ child.title }}
                </v-list-item-title>
              </v-list-item-content>
            </v-list-item>
          </v-list-group>

          <v-list-item v-else :key="item.title" :to="item.to" router exact>
            <v-list-item-action>
              <v-icon>{{ item.icon }}</v-icon>
            </v-list-item-action>
            <v-list-item-content>
              <v-list-item-title v-text="item.title" />
            </v-list-item-content>
          </v-list-item>
        </template>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar
      dark
      :clipped-left="$vuetify.breakpoint.lgAndUp"
      app
      color="#253b7f"
    >
      <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
      <!-- <v-btn icon @click.stop="miniVariant = !miniVariant">
        <v-icon>mdi-{{ `chevron-${miniVariant ? 'right' : 'left'}` }}</v-icon>
      </v-btn> -->
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
      drawer: null,
      items: [
        {
          icon: 'mdi-apps',
          title: 'Dashboard',
          to: '/',
        },
        {
          icon: 'mdi-chart-line',
          title: 'Đánh giá danh hiệu',
          children: [
            {
              icon: 'mdi-upload',
              title: 'Tải file excel',
              to: '/index2',
            },
          ],
        },
        {
          icon: 'mdi-chart-bar',
          title: 'Thống kê danh hiệu',
          to: '/inspire',
        },
      ],
      title: 'Xét Khen Thưởng',
    }
  },
}
</script>
