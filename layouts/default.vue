<template>
<div>
    <Navbar />
    <slot /> 
      
</div>
</template>

<script setup>
definePageMeta({
  layout: "sample",
});
</script>