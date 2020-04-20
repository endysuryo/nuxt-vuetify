<template>
  <v-app dark>
    <!-- start of profile dialog -->
    <v-dialog v-model="dialog" max-width="290">
      <v-card>
        <div align="center">
          <v-list-item-avatar height="150" width="150">
            <img src="https://randomuser.me/api/portraits/men/81.jpg" />
          </v-list-item-avatar>
        </div>
        <!-- <v-card-title class="headline text-center">Endy Suryo</v-card-title> -->
        <v-card-text class="headline text-center">Paijo Pratama</v-card-text>
        <v-card-text class="text-center">Join 06 July 2011</v-card-text>

        <v-card-actions>
          <v-spacer></v-spacer>

          <v-btn color="blue" text @click="dialog = false">Account</v-btn>

          <v-btn color="blue" icon @click="dialog = false">
            <v-icon dark>mdi-power</v-icon>
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
    <!-- end of profile dialog -->
    <v-navigation-drawer
      v-model="drawer"
      :mini-variant="miniVariant"
      :clipped="clipped"
      fixed
      app
    >
      <v-img
        :aspect-ratio="16 / 9"
        src="https://cdn.vuetifyjs.com/images/parallax/material.jpg"
      >
        <v-row align="end" class="lightbox white--text pa-2 fill-height">
          <v-col>
            <div class="subheading">Paijo Pratama</div>
            <div class="body-1">paijopratama@gmail.com</div>
          </v-col>
        </v-row>
      </v-img>
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
        <hr class="my-3" />
        <v-list-item>
          <v-switch
            v-model="$vuetify.theme.dark"
            inset
            primary
            label="Dark Mode"
          />
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar :clipped-left="clipped" fixed app>
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      <v-toolbar-title v-text="title" />
      <v-spacer />
      <v-btn
        class="mx-2"
        fab
        dark
        small
        color="blue"
        @click.stop="dialog = true"
      >
        <v-icon dark>mdi-account</v-icon>
      </v-btn>
    </v-app-bar>
    <v-content>
      <v-container>
        <nuxt />
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      dialog: false,
      clipped: true,
      drawer: false,
      fixed: false,
      items: [
        {
          icon: 'mdi-apps',
          title: 'Welcome',
          to: '/'
        },
        {
          icon: 'mdi-chart-bubble',
          title: 'Inspire',
          to: '/inspire'
        },
        {
          icon: 'mdi-microsoft',
          title: 'Contribute',
          to: '/contribute'
        }
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: 'Prototype'
    }
  }
}
</script>
