<template>
  <default-layout>
    <template>
      <nota-editor />
    </template>
  </default-layout>
</template>

<script>
import DefaultLayout from "@/components/layouts/DefaultLayout.vue";
import NotaEditor from "@/components/NotaEditor.vue";
export default {
  components: {
    DefaultLayout,
    NotaEditor,
  },
};
</script>
