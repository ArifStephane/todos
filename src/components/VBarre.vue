<template>
  <div class="flex justify-center mb-10">
    <input
      v-model="todo"
      class="w-2/4 h-12 border border-solid rounded-3xl pl-3 shadow-lg"
      placeholder="Add todo..."
      @keyup.enter="emitAddElementEvent"
    />
    <button class="-ml-12 pt-1">
      <AjoutIcon @click="emitAddElementEvent" />
    </button>
  </div>
</template>
<script setup>
import { ref } from "vue";
import AjoutIcon from "@/components/icons/AjoutIcon.vue";

const todo = ref("");
const emits = defineEmits(["addElement"]);

function emitAddElementEvent() {
  emits("addElement", todo.value);
  todo.value = "";
}
</script>
