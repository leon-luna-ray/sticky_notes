<script setup>
const client = useSupabaseClient();
const user = useSupabaseUser();

const logout = async () => {
    await client.auth.signOut();
}
onMounted(() => {
    watchEffect(() => {
        if (!user.value) {
            navigateTo('/login')
        }
    })
});
</script>
<template>
    <div id="notes-page" class="page">
        <h1>Notes Page</h1>
        <button @click="logout">Logout</button>
    </div>
</template>