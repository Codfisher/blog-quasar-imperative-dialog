<script
  setup
  lang="ts"
>
import CreateForm from './components/create-form.vue';

import { openUsingDialog } from './common/utils-quasar';

function openEditForm() {
  const dialog = openUsingDialog(CreateForm, {
    'onUpdate:modelValue'() {
      alert('送出資料');

      dialog.hide();
    }
  });
}

function openEditFormBottom() {
  const dialog = openUsingDialog(CreateForm, {
    'onUpdate:modelValue'() {
      alert('送出資料');

      dialog.hide();
    }
  }, {
    position: 'bottom',
  });
}
</script>

<template>
  <div class="fit flex flex-col">
    <create-form />

    <q-btn
      label="開啟 Dialog"
      class="mt-2"
      no-caps
      @click="openEditForm()"
    />

    <q-btn
      label="在底部開啟 Dialog"
      class="mt-2"
      no-caps
      @click="openEditFormBottom()"
    />
  </div>
</template>

<style scoped></style>
