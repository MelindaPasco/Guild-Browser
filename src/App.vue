<script setup lang="ts">
  import { ref } from 'vue';
  import GuildmateList from './components/GuildmateList.vue';
  import Mate from './types/Mate';
  import OrderTerm from './types/OrderTerm';

  const mates = ref<Mate[]>([
    { nickname: 'Nikoline', level: 4, role: 'Druid', id: 1},
    { nickname: 'Rei', level: 7, role: 'Fighter', id: 2},
    { nickname: 'Ssazhias', level: 20, role: 'Bard', id: 3},
    { nickname: 'SLD-38974', level: 5, role: 'Cleric', id: 4},
    { nickname: 'Nisk', level: 13, role: 'Monk', id: 5},
    { nickname: 'Safeguard', level: 16, role: 'Fighter', id: 6},
    { nickname: 'Sharaï', level: 16, role: 'Warlock', id: 7},
    { nickname: 'Mocha', level: 20, role: 'Cleric', id: 8},
    { nickname: 'Yuna', level: 11, role: 'Druid', id: 9},
    { nickname: 'Mrran', level: 4, role: 'Barbarian', id: 10},
    { nickname: 'Arikel', level: 20, role: 'Bard', id: 11}
  ])

  const order = ref<OrderTerm>('nickname')

  const handleClick = (term: OrderTerm) => {
    order.value = term
  }
</script>

<template>
  <header>
    <div class="title">
      <h1>Guild Browser</h1>
    </div>
  </header>
  <div class="order">
    <button @click="handleClick('nickname')">Order by Nickname</button>
    <button @click="handleClick('level')">Order by Level</button>
    <button @click="handleClick('role')">Order by Role</button>
  </div>

  <GuildmateList :mates="mates" :order="order"/>
</template>

<style>
  @import url('https://fonts.cdnfonts.com/css/satoshi');
  body{
    background-color: #212121;
    color: #BB86FC;
    font-family: 'Satoshi', sans-serif;
  }
  button {
    margin: 4px;
    background-color: #BB86FC;
  }

  li {
    background-color: #2e2e2e;
    padding: 6px;
    border-radius: 10px;
    margin-bottom: 10px;
  }
  li h2 {
    margin: 0 0 10px 0;
  }
  li p {
    margin: 0;
  }

  li.Barbarian::marker {
    content: '🤬';
  }
  li.Bard::marker {
    content: '🎸';
  }
  li.Cleric::marker {
    content: '❤️‍🩹';
  }
  li.Druid::marker {
    content: '🌳';
  }
  li.Fighter::marker {
    content: '⚔️';
  }
  li.Monk::marker {
    content: '🤛';
  }
  li.Warlock::marker {
    content: '🪄';
  }
</style>
