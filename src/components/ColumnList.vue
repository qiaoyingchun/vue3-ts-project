<template>
    <div class="container">
         <div class="row align-items-start">
            <div class="col-4 mb-3" v-for="column in columnList" :key="column.id">
                <div class="card">
                    <img :src="column.avatar" :alt="column.title" class="round-cirle border border-light w-25 my-3 img_center"/>
                    <div class="card-body">
                        <h5 class="card-title">{{ column.title }}</h5>
                        <p class="card-text">{{ column.description }}</p>
                        <a href="#" class="btn btn-outline-primary">进入专栏</a>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
<script lang="ts">
import { computed, defineComponent, PropType } from 'vue'
export interface ColumnProps {
    id: number;
    title: string;
    avatar?: string;
    description: string;
}
export default defineComponent({
    name: 'ColumnList',
    props: {
        list: {
            type: Array as PropType<ColumnProps[]>,
            required: true
        }
    },
    setup (props) {
        const columnList = computed(() => {
            return props.list.map(column => {
                if (!column.avatar) {
                    column.avatar = require('@/assets/column.png')
                }
                return column
            })
        })
        return {
            columnList
        }
    }
})
</script>
<style lang="scss" scoped>
.img_center{
    margin: 0 auto;
}
</style>
