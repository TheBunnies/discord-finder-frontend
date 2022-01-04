<template>
<q-input class="q-mb-sm" width="100%" v-model="text" label="Please input an id..." rounded></q-input>
<div class="full-width column wrap items-center">
    <button class="btn" @click="submitInput" :disabled="!text && text.length < 1"><slot></slot></button>
</div>

</template>

<script>
import {defineComponent, ref} from 'vue';
export default defineComponent( {
    name: 'UserInput',
    emits: ['submit'],
    setup(props, { emit }) {
        const text = ref('');

        
        const submitInput = () => {
            emit('submit', text.value);
        }
        return { text, submitInput }
    }
    
})
</script>

<style lang="sass" scoped>
.btn 
  padding: 10px 15px
  background: none
  color: pink
  border: 3px solid pink
  cursor: pointer
  width: 100%

.btn:hover
    background: hotpink
    transition: 0.7s
</style>
