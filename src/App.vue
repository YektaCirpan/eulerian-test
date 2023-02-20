<script setup lang="ts">
import { reactive } from "vue";
import TreeView from "./components/TreeView.vue";

const tree = reactive({
  firstname: "john",
  lastname: "doe",
  location: {
    address: "lorem ipsum dolor sit amet",
    zipcode: "XXXX",
  },
  cart: ["apple", "banana", "coconut"],
  null: null,
});
</script>

<template>
  <main>
    <v-container>
      <v-img class="mb-5" width="300" src="eulerian.png" alt="eulerian logo" />
      <v-row>
        <v-col cols="6">
          <v-sheet border rounded class="pa-5" color="grey-lighten-3">
            {{ tree }}
          </v-sheet>
        </v-col>
        <v-col cols="6">
          <v-card>
            <v-list>
              <TreeView :tree="tree" />
            </v-list>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </main>
</template>
