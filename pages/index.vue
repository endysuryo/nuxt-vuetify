<template>
  <v-container>
    <v-row dense>
      <v-col cols="12">
        <v-card class="mx-auto text-center" dark>
          <v-card-text>
            <v-sheet color="rgba(0, 0, 0, .12)">
              <v-sparkline
                :value="value"
                color="rgba(255, 255, 255, .7)"
                height="100"
                padding="24"
                stroke-linecap="round"
                smooth
              >
                <template v-slot:label="item">${{ item.value }}</template>
              </v-sparkline>
            </v-sheet>
          </v-card-text>

          <v-card-text>
            <div class="display-1 font-weight-thin">Sales Last 24h</div>
          </v-card-text>
          <v-divider></v-divider>

          <v-card-actions class="justify-center">
            <v-btn block text nuxt to="/inspire">Go to Report</v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  data() {
    return {
      value: [423, 446, 675, 510, 590, 610, 0]
    }
  }
})
</script>
