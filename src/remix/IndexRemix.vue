<template>
  <div class="bg-white h-screen">
    <div
      class="text-gray-300 lowercase text-8xl text-center pt-40 mb-16 font-semibold leading-4 tracking-wide"
    >
      todos
    </div>
    <VBarre @addElement="addToDo" />
    <div class="flex justify-center flex-col max-w-lg mx-auto">
      <div class="">
        <span class="font-bold">En cours</span>
        <div v-for="todo in allToDo" :key="todo">
          <VTasks
            :todo="todo"
            @deleteElement="deleteToDo"
            @clickElement="addToFinish"
          />
        </div>
      </div>
      <div>
        <span class="font-bold">Terminer</span>

        <div v-for="todo in finishToDo" :key="todo">
          <VTasks :todo="todo" @deleteElement="addToFinish" :validated="true" />
        </div>
      </div>
    </div>
  </div>
</template>
<script setup>
import { ref } from "vue";
import VBarre from "@/components/VBarre.vue";
import VTasks from "@/components/VTasks.vue";

const allToDo = ref([]);
const finishToDo = ref([]);
function addToDo(todo) {
  if (todo == "") {
    alert("Please write item");
    return;
  }
  allToDo.value.push(todo);
  console.log("allToDo", allToDo);
}

function deleteToDo(todo) {
  console.log("voila", todo);
  const index = allToDo.value.indexOf(todo);
  console.log("hsxhxshgh", index);
  if (index >= 0) allToDo.value.splice(index, 1);
}

function addToFinish(todo) {
  finishToDo.value.push(todo);
  console.log(todo);
  deleteToDo(todo);
}
</script>

<style lang="scss" scoped></style>
