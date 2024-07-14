<template>
  <q-card>
    <q-card-section class="bg-teal text-white">
      建立資料
    </q-card-section>

    <q-form @submit="handleSubmit">
      <q-card-section>
        <q-input
          v-model="modelValue.name"
          label="名稱"
          outlined
        ></q-input>

        <q-btn
          label="送出"
          type="submit"
          color="teal"
          class="mt-2 fit"
        />
      </q-card-section>
    </q-form>
  </q-card>
</template>

<script
  setup
  lang="ts"
>
import { ref } from 'vue';

interface Props {
  modelValue?: {
    name: string;
  };
}
const props = withDefaults(defineProps<Props>(), {
  modelValue: () => ({
    name: '',
  }),
});

const emit = defineEmits<{
  (e: 'update:modelValue', value: NonNullable<Props['modelValue']>): void;
}>();

const modelValue = ref({ ...props.modelValue });

function handleSubmit() {
  emit('update:modelValue', modelValue.value);
}
</script>

<style
  scoped
  lang="sass"
></style>
