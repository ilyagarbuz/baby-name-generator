<template>
    <div class="option-container">
        <h4>{{option.title}}</h4>
        <div class="options-buttons">
          <button v-for="(value, index) in option.buttons" 
          :key="value" @click="options[option.category] = value" 
          class="option" 
          :class="computedButtonClasses(value, index)"
          >{{value}}</button>
        </div>
    </div>
</template>

<script setup lang="ts">
import { Gender, Length, Popularity } from "@/data";


interface OptionProps {
    option: {
        title: string;
        category: string,
        buttons: Gender[] | Popularity[] | Length[]
    },
    options: {
        gender: Gender,
        popularity: Popularity,
        length: Length,
    }
}

const computedButtonClasses = (value, index) => {
    const classes = []
    if(value === props.options[props.option.category]) classes.push('option-active')
    if(index === 0) classes.push('option-left')
    if(index === props.option.buttons.length - 1) classes.push('option-right')
    return classes.join(' ')
}

const props = defineProps<OptionProps>()

</script>