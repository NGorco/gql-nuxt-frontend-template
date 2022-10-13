<script setup>
const query = {query: `
  {getUser {
    user_id
    user_name
    user_description
    user_password
    user_verification_code
    user_status
    user_email
  }}
`};
const conf = useRuntimeConfig();
console.log(conf);
const {data: {getUser: {user_id}}} = await $fetch(conf.graphqlurl, {
  body: JSON.stringify(query),
  method: 'POST',
  headers: { "Content-Type": "application/json" },
});
</script>
<template>
  <div>
    <h1>Hello!</h1> {{user_id}}
  </div>
</template>