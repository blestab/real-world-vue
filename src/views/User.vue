<template>
    <h1>This is {{ username }}'s profile page</h1>
</template>

<script>
export default {
    props: {
        username: {
            type: String,
        },
    },
}
</script>