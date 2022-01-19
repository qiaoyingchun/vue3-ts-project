<template>
    <div class="dropdown" ref="dropudownRef">
        <button class="btn btn-secondary dropdown-toggle" type="button"
        id="dropdownMenuButton1" data-bs-toggle="dropdown" aria-expanded="false" @click.prevent="toogleOpen">
            {{ title }}
        </button>
        <ul class="dropdown-menu" aria-labelledby="dropdownMenuButton1" :style="{display : 'block'}" v-if="isOpen">
            <slot></slot>
        </ul>
</div>
</template>
<script lang="ts">
import { defineComponent, ref, watch } from 'vue'
import useClickOutside from '@/hooks/UseClickOutside'
export default defineComponent({
    name: 'DropDown',
    props: {
        title: {
            type: String,
            required: true
        }
    },
    setup () {
        const isOpen = ref(false)
        const dropudownRef = ref<HTMLElement | null>(null)
        const toogleOpen = () => {
            console.log(isOpen.value)
            isOpen.value = !isOpen.value
        }
        const isClickOutside = useClickOutside(dropudownRef)
        watch(isClickOutside, () => {
            if (isOpen.value && isClickOutside.value) {
                isOpen.value = false
            }
        })
        return {
            isOpen,
            toogleOpen,
            dropudownRef
        }
    }
})
</script>
