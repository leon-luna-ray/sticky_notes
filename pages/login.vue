<script setup>
const client = useSupabaseClient();
const user = useSupabaseUser();

// State
const email = ref('');
const password = ref('');

// Methods
const login = async () => {
    const { user, error } = await client.auth.signInWithPassword({
        email: email.value,
        password: password.value,
    })
}

onMounted(() => {
    watchEffect(()=>{
        if(user.value) {
            navigateTo('/notes')
        }
    })
})
</script>
<template>
    <div id="login" class="page">
        <div class="login-box">
            <div class="title">
                <h1>Existing User</h1>
            </div>
            <form @submit.prevent="() => (login())">
                <div class="inner ">
                    <input type="email" placeholder="Email" v-model="email">
                    <input type="password" placeholder="Password" v-model="password">
                    <button @click="submit">Login</button>
                    <NuxtLink to="/sign-up"><span>New user? Sign up here.</span></NuxtLink>
                </div>
            </form>
        </div>
    </div>
</template>