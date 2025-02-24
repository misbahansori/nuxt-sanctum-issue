<script setup lang="ts">
const { data: users } = await useSanctumFetch<any>("/api/users");

console.log(users.value);
</script>

<template>
  <div>
    <h1>Users</h1>
    <ul>
      <li v-for="user in users" :key="user.id">
        <NuxtLink :to="`/user/${user.id}`"> {{ user.name }} </NuxtLink>
      </li>
    </ul>
  </div>
</template>
