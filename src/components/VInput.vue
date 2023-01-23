<template>
  <div class="flex justify-center mb-10 cursor-pointer">
    <input
      v-model="todo.label"
      class="w-2/4 h-12 border border-solid rounded-3xl pl-3 shadow-lg"
      placeholder="Add todo..."
      @keyup.enter="emitAddElementEvent"
    />
    <button class="-ml-12 pt-1" @click="emitAddElementEvent">
      <AjoutIcon />
    </button>
  </div>
</template>
<script setup>
import { ref, defineEmits } from "vue";
import AjoutIcon from "@/components/icons/AjoutIcon.vue";

const emits = defineEmits(["addElement"]);

const todo = ref({ state: "progress", label: "" });

function emitAddElementEvent() {
  emits("addElement", todo.value);
  todo.value = { state: "progress", label: "" };
}
</script>
