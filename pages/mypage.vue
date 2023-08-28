<template>
    <div class="text-center" role="alert">
        <h1 class="p-4">マイページ</h1>
        <ul>
            <li>ユーザーネーム：{{ user.name }}</li>
            <li>会社名：{{ user.company }}</li>
        </ul>
    </div>
    <Nuxt-link to="/ImagePage">前へ</Nuxt-link>
</template>
<script setup>

const user =userInformation();
</script>