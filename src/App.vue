<script
  setup
  lang="ts"
>
import CreateForm from './components/create-form.vue';
import { openUsingDialog } from './common/utils-quasar';
import { useQuasar, QDialog } from 'quasar';
import { h } from 'vue';

const $q = useQuasar();

function openEditFormWithH() {
  const dialogProp = {};

  const dialog = $q.dialog({
    component: h(
      QDialog,
      dialogProp,
      {
        default: () => h(CreateForm, {
          'onUpdate:modelValue'() {
            alert('送出資料');
            dialog.hide();
          },
          onCancel() {
            dialog.hide();
          }
        })
      }
    )
  });
}

function openEditForm() {
  const dialog = openUsingDialog(CreateForm, {
    'onUpdate:modelValue'() {
      alert('送出資料');

      dialog.hide();
    },
    onCancel() {
      dialog.hide();
    }
  });
}

function openEditFormBottom() {
  const dialog = openUsingDialog(CreateForm, {
    'onUpdate:modelValue'() {
      alert('送出資料');
      dialog.hide();
    },
    onCancel() {
      $q.notify({
        message: '確定取消？',
        timeout: 3000,
        progress: true,
        actions: [
          {
            label: '確定',
            color: 'white',
            handler: () => {
              dialog.hide();
            }
          }
        ]
      })
    }
  }, {
    position: 'bottom',
    // 不允許點擊外部關閉
    persistent: true,
  });
}
</script>

<template>
  <div class="fit flex flex-col gap-4">
    <create-form />

    <q-card>
      <q-card-section class="bg-teal-5 text-white">
        自行組合 Dialog
      </q-card-section>

      <div class="flex flex-col p-4">
        <q-btn
          label="開啟 Form"
          class="mt-2"
          no-caps
          @click="openEditFormWithH()"
        />
      </div>
    </q-card>

    <q-card>
      <q-card-section class="bg-teal text-white">
        使用 openUsingDialog
      </q-card-section>

      <div class="flex flex-col p-4">
        <q-btn
          label="開啟 Form"
          class="mt-2"
          no-caps
          @click="openEditForm()"
        />

        <q-btn
          label="在底部開啟 Form"
          class="mt-2"
          no-caps
          @click="openEditFormBottom()"
        />
      </div>
    </q-card>


  </div>
</template>

<style scoped></style>
