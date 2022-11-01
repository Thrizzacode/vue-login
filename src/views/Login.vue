<template>
    <div class="container mt-5">
        <form class="row justify-content-center" @submit.prevent="signIn">
            <div class="col-md-6">
                <h1 class="h3 mb-3 font-weight-normal">請先登入</h1>
                <div class="mb-2">
                    <label for="inputEmail" class="sr-only">Email address</label>
                    <input v-model="user.username" type="email" id="inputEmail" class="form-control"
                        placeholder="Email address" required autofocus />
                </div>
                <div class="mb-2">
                    <label for="inputPassword" class="sr-only">Password</label>
                    <input v-model="user.password" type="password" id="inputPassword" class="form-control"
                        placeholder="Password" required />
                </div>

                <div class="text-end mt-4">
                    <button class="btn btn-lg btn-primary btn-block" type="submit">登入</button>
                </div>
            </div>
        </form>
    </div>
</template>
<script setup>
import { onMounted, reactive, watch, watchEffect } from 'vue';
import { inject } from 'vue';
import { useRouter } from 'vue-router';

const axios = inject('axios');
const router = useRouter();

const user = reactive({
    username: '',
    password: '',
})

const signIn = () => {
    const api = `${import.meta.env.VITE_APP_API}admin/signin`
    console.log(api);
    axios.post(api, user)
        .then((res) => {
            if (res.data.success) {
                const { token, expired } = res.data;
                // console.log(token, expired);
                document.cookie = `hexToken=${token}; expires=${new Date(expired)}`;
                router.push('/dashboard')
            }
        })

}


</script>