<script setup lang="ts">
const props = defineProps<{
  tree: Object;
}>();

function updateValueOfKey(key: keyof Object, value: any) {
  // eslint-disable-next-line vue/no-mutating-props
  props.tree[key] = value;
}
</script>

<template>
  <template :key="key" v-for="(value, key) in tree">
    <v-list-item v-if="typeof value !== 'object' || value === null">
      <label>{{ key }}:</label>
      <input
        type="text"
        v-bind:value="value || key"
        @input="updateValueOfKey(key, $event.target?.value)"
        class="ml-1 px-1"
      />
    </v-list-item>
    <v-list-group :value="key" v-else>
      <template v-slot:activator="{ props }">
        <v-list-item v-bind="props" class="font-weight-bold">
          {{ key }}
        </v-list-item>
      </template>
      <TreeView :tree="value" />
    </v-list-group>
  </template>
</template>
