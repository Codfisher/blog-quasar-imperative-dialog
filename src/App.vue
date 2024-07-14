<script setup lang="ts">
import DialogTemp from './components/DialogTemp.vue';

import { openUsingDialog } from './common/utils-quasar';

function openEditForm() {
  openUsingDialog(DialogTemp);
}
</script>

<template>
  <div>安安</div>

  <q-btn @click="openEditForm()">按鈕</q-btn>
</template>

<style scoped></style>
