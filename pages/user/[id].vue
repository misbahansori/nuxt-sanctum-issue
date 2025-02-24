<script setup lang="ts">
const route = useRoute();

// This is not working
const { data: user } = await useSanctumFetch<any>(
  `/api/users/${route.params.id}`
);

// This is working
// const { data: user } = await useLarafetch<any>(`/api/users/${route.params.id}`);

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
    <strong>Refresh the page to see the error</strong>
    <pre> {{ user }} </pre>
  </div>
</template>
