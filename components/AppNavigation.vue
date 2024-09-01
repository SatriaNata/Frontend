<template>
    <div></div>
</template>

<script setup>
    const {data: games} = await useFetch(" https://www.mmobomb.com/api1/games?platform=pc");
</script>

<style lang="scss" scoped></style>