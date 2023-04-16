<script setup>
import { ref, watch } from "vue";
import { defineProps, defineEmits } from "vue";

const props = defineProps({
    modelValue: String,
});

const emit = defineEmits(["update:modelValue"]);

const searchhTerm = ref(props.modelValue);
watch(searchhTerm,newValue => {
    emit("update:modelValue", newValue);
});


</script>


<template>
    <div class="filter">
        <input type="text" v-model="searchhTerm" class="form-control" placeholder="search a beer">
        
    </div>
</template>