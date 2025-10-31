<script setup>
import Button from "./Button.vue";
import { ref } from "vue";

const emit = defineEmits({
  selectCity(payload) {
    console.log("Payload in emit validator:", payload);
    return payload ? true : false;
  },
});
let isEdited = ref(false);
function select() {
  isEdited.value = false;
  emit("selectCity", "London");
}

function edit() {
  isEdited.value = true;
}
</script>

<template>
  {{ isEdited }}
  <Button @click="edit()">
    <img src="../assets/location.svg" alt="Icon Location" />
    Change city
  </Button>
  <input type="text" placeholder="Enter city name" />

  <Button @click="select()">Save</Button>
</template>
