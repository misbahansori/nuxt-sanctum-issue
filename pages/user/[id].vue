<script setup lang="ts">
const route = useRoute();
const { data: user } = await useSanctumFetch<any>(
  `/api/users/${route.params.id}`
);

console.log(user.value);

if (!user.value) {
  throw createError({
    statusCode: 404,
    message: "User not found",
    fatal: true,
  });
}
</script>

<template>
  <div>
    <h1>User</h1>
    <pre> {{ user }} </pre>
  </div>
</template>
