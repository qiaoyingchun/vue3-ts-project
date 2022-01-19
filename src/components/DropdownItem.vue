<template>
    <li class="dropdown-option"
    :class="{'is-disbled' : disabled }">
        <slot></slot>
    </li>
</template>
<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
    name: 'DropdownItem',
    props: {
        disabled: {
            type: Boolean,
            required: false
        }
    }
})
</script>
<style lang="scss" scoped>
.dropdown-option.is-disbled{
    pointer-events: none;
    background-color: transparent;
    color: #6c5c7d !important;
}
</style>
