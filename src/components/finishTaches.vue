<template>
  <div class="flex justify-between space-y-5 items-center mb-10">
    <input
      type="checkbox"
      id="Catégorie"
      name="fait"
      class="mr-3"
      :todo="todo"
      @click="emitdeletElementEvent"
    />
    <span>
      {{ todo }}
    </span>
  </div>
</template>
<script setup>
import { ref, defineEmits, defineProps } from "vue";
const todo = ref("");
const props = defineProps(["todo"]);
const emits = defineEmits(["deleteElement"]);
function emitdeletElementEvent() {
  emits("deletElement", props.todo);
  todo.value = "";
}
</script>
