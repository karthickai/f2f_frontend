<template>
  <v-app-bar color="primary" dark flat="true" app>
    <v-img class="mx-3 mt-6" src="@/assets/logo.png" max-height="150" max-width="200" contain></v-img>

    <v-spacer />
    <v-toolbar-items>
      <v-menu offset-y origin="center center" transition="scale-transition">
        <template v-slot:activator="{ on }">
          <v-btn icon large text slot="activator" v-on="on">
            <v-avatar size="32px">
              <img src="@/assets/man_4.jpg" alt="Michael Wang" />
            </v-avatar>
          </v-btn>
        </template>
        <v-list class="pa-0">
          <v-list-item
            v-for="(item, index) in profileMenus"
            :to="!item.href ? { name: item.name } : null"
            :href="item.href"
            @click="item.click"
            ripple="ripple"
            :disabled="item.disabled"
            :target="item.target"
            rel="noopener"
            :key="index"
          >
            <v-list-item-action v-if="item.icon">
              <v-icon>{{ item.icon }}</v-icon>
            </v-list-item-action>
            <v-list-item-content>
              <v-list-item-title>{{ item.title }}</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list>
      </v-menu>
    </v-toolbar-items>
  </v-app-bar>
</template>
<script>
export default {
  name: 'AppToolbar',
  components: {},
  data() {
    return {
      profileMenus: [
        {
          icon: 'account_circle',
          href: '#',
          title: 'Profile',
          click: this.handleProfile
        },
        {
          icon: 'settings',
          href: '#',
          title: 'Settings',
          click: this.handleSetting
        },
        {
          icon: 'fullscreen_exit',
          href: '#',
          title: 'Logout',
          click: this.handleLogut
        }
      ]
    }
  },
  computed: {},
  methods: {
    handleLogut() {
      //   this.$router.push('/auth/login')
    },
    handleSetting() {},
    handleProfile() {}
  },
  created() {}
}
</script>

<style lang="sass" scoped></style>
