<template>
  <div class="flex justify-between space-y-5 items-center mb-10">
    <div>
      <input
        type="checkbox"
        id="Catégorie"
        name="fait"
        class="mr-3"
        :todo="todo"
        @click="emitclickElementEvent"
      />
      <span :class="{ 'line-through italic': todo.state == 'finish' }">
        {{ todo.label }}
      </span>
    </div>
    <button class="ml-72 bg-slate-300 p-4 rounded-full">
      <DeleteIcon @click="emitdeleteElementEvent" />
    </button>
  </div>
</template>
<script setup>
import { ref, defineEmits, defineProps } from "vue";
import DeleteIcon from "@/components/icons/DeleteIcon.vue";

const props = defineProps(["todo"]);
const emits = defineEmits(["deleteElement", "clickElement"]);
function emitdeleteElementEvent() {
  emits("deleteElement", props.todo);
}

function emitclickElementEvent() {
  emits("clickElement", props.todo);
}
</script>
