<template>
    <div>
        Dashboard
    </div>
</template>

<script setup>
import { inject } from 'vue';
import { useRouter } from 'vue-router';

const axios = inject('axios');
const router = useRouter();

const token = document.cookie.replace(/(?:(?:^|.*;\s*)hexToken\s*=\s*([^;]*).*$)|^.*$/, '$1');
// console.log(token);
axios.defaults.headers.common['Authorization'] = token;
const api = `${import.meta.env.VITE_APP_API}api/user/check`
console.log(api);
axios.post(api)
    .then((res) => {
        if(!res.data.success)
       router.push('/login')
    })
</script>