<template>
  <div class="bg-white h-screen">
    <div
      class="text-gray-300 lowercase text-8xl text-center pt-40 mb-16 font-semibold leading-4 tracking-wide"
    >
      todos
    </div>
    <VInput @addElement="addToDo" />
    <div class="flex justify-center flex-col max-w-lg mx-auto">
      <div class="">
        <span class="font-bold">En cours</span>
        <div v-for="todo in allToDo" :key="todo">
          <VTaches
            :todo="todo"
            @deleteElement="deleteToDo"
            @clickElement="addToFinish"
          />
        </div>
      </div>
    </div>
  </div>
</template>
<script setup>
import { ref } from "vue";
import VInput from "@/components/VInput.vue";
import VTaches from "@/components/VTaches.vue";

const allToDo = ref([]);

function addToDo(todo) {
  if (todo.label == "") {
    alert("Please write item");
    return;
  }

  allToDo.value.push(todo);
  console.log(allToDo);
}

function deleteToDo(todo) {
  console.log("voila", todo);
  const index = allToDo.value.indexOf(todo);
  console.log("hsxhxshgh", index);
  if (index >= 0) allToDo.value.splice(index, 1);
}

function addToFinish(todo) {
  console.log(todo);
  if (todo.state == "finish") {
    todo.state = "progress";
    return;
  }
  todo.state = "finish";
}
</script>
<style lang="scss" scoped></style>
