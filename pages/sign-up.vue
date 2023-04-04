<script setup>
const client = useSupabaseClient();

// State
const email = ref('');
const password = ref('');

// Methods
const signUp = async () => {
    const { user, error } = await client.auth.signUp({
        email: email.value,
        password: password.value,
    })
}
</script>
<template>
    <div id="signup" class="page">
        <div class="login-box">
            <div class="title">
                <h1>New User</h1>
            </div>
            <form @submit.prevent="() => (signUp())">
                <div class="inner ">
                    <input type="email" placeholder="Email" v-model="email">
                    <input type="password" placeholder="Password" v-model="password">
                    <button @click="submit">Sign Up</button>
                    <NuxtLink to="/login">
                        <span>Existing user? Click here to login.</span>
                    </NuxtLink>
                </div>
            </form>
        </div>
    </div>
</template>