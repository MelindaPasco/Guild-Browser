<script setup lang="ts">
import { PropType, computed } from '@vue/runtime-core';
import Mate from '../types/Mate';
import OrderTerm from '../types/OrderTerm';

const props = defineProps({
    mates: {
        type: Array as PropType<Mate[]>,
        required: true
    },
    order: {
        type: String as PropType<OrderTerm>,
        required: true
    }
})

const orderedMates = computed(() => {
    return [...props.mates].sort((a: Mate, b: Mate) => {
        return a[props.order] > b[props.order] ? 1 : -1
    })
})

</script>

<template>
    <div class="guildmate-list">
        <p class="order">Ordered by {{ order }}</p>
        <transition-group name="list" tag="ul">
            <li v-for="mate in orderedMates" :key="mate.id" :class=mate.role >
                <h2>{{ mate.nickname }}</h2>
                <div>
                    <p><b>{{ mate.role}}</b> level {{mate.level}}</p>
                </div>
            </li>
        </transition-group>
    </div>
</template>

<style scoped>
    .order {
        text-align: right;
    }
    .list-move {
        transition: all 1s;
    }
</style>