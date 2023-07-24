<!-- ImagePage.vue -->
<template>
  <div>
    <!-- ナビゲーションバー -->
    <nav class="bg-dark text-white">
      <ul class="list-inline">
        <li class="list-inline-item"><nuxt-link to="/">財務会計アプリ</nuxt-link></li>
        <li class="list-inline-item"><nuxt-link to="/ImagePage">複数ページ</nuxt-link></li>
      </ul>
    </nav>

    <!-- 画像を表示する -->
    <h1>なにもないよ</h1>
    <img src="https://image.itmedia.co.jp/nl/articles/1705/03/l_enjin_170502mameshiba01.jpg" alt="Image" />
    <!-- 戻るリンク -->
    <nuxt-link to="/">戻る</nuxt-link>
  </div>
</template>

<script setup>

</script>
