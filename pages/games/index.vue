<template> 
    <div v-if="status==='pending'">
        <p>Loading...</p>
    </div>
    <div v-else-if="error">
        <p>Error Code {{ error.statusCode }}</p>
        <p>Error Message {{  error.message }}</p>
    </div>
    <div v-else>
        <!-- <button @click="refresh"> Refresh Data</button> -->
        <div class="grid grid-cols-5 gap-4">
        <div 
            v-for="game in games"
            class="flex flex-col shadow-md bg-white p-6 rounded-md"
        >
            <img class="w-[75px] h-auto self-center" :src="game.thumbnail" alt="">
            <NuxtLink :to="{ name: 'games-id', params: { id: game.id } }">{{ game.title }}</NuxtLink>
        </div>
    </div>
    </div>
    
    
</template>

<script setup>
    const {
        status,
        data: games,
        refresh,
        error
    } = useFetch(
        "https://www.mmobomb.com/api1/games?platform=pc"
        // "https://fakestoreapi.com/products"
        ,{
        lazy: false,
        transform: (games) => {
            return games.map((game) => ({
                id: game.id,
                title: game.title,
                thumbnail: game.thumbnail,
                short_description: game.short_description,
                game_url: game.game_url,
                genre: game.genre,
                platform: game.platform,
                publisher: game.publisher,
                developer: game.developer,
                release_date: game.release_date,
                profile_url: game.profile_url
            }))
        }
    });

    watch(error, value => {
        if(value) refresh()
    })
    
</script>

<style lang="scss" scoped></style>