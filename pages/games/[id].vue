<template>
    <div class="flex justify-center max-h-96 xl:max-h-[600px]">
        <div>
            <div
                class="w-full max-w-sm bg-white border border-gray-200 rounded-lg shadow dark:bg-gray-800 dark:border-gray-700">
                <div class="flex flex-col items-center pb-10">
                    <h2>{{ game?.title || '-' }}</h2>
                    <img class="w-24 h-24 mb-3 rounded-full shadow-lg" :src="game?.thumbnail" alt="Bonnie image" />
                    <h5 class="mb-1 text-xl font-medium text-gray-900 dark:text-white">{{ game?.short_description || '-'}}</h5>
                    <h5 class="mb-1 text-xl font-medium text-gray-900 dark:text-white">{{ game?.genre || '-'}}</h5>
                    <h5 class="mb-1 text-xl font-medium text-gray-900 dark:text-white">{{ game?.platform || '-'}}</h5>
                    <h5 class="mb-1 text-xl font-medium text-gray-900 dark:text-white">{{ game?.publisher || '-'}}</h5>
                    <h5 class="mb-1 text-xl font-medium text-gray-900 dark:text-white">{{ game?.developer || '-'}}</h5>
                    <h5 class="mb-1 text-xl font-medium text-gray-900 dark:text-white">{{ game?.release_date || '-'}}</h5>
                    <div class="flex mt-4 md:mt-6">
                        <NuxtLink :to="game?.profile_url" class="inline-flex items-center px-4 py-2 text-sm font-medium text-center text-white bg-blue-700 rounded-lg hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800">Game Profile</NuxtLink>
                    </div>
                </div>

            </div>
        </div>

    </div>
</template>

<script setup>
const { id } = useRoute().params
const uri = 'https://www.mmobomb.com/api1/game?id=' + id


const { data: game } = await useFetch(uri, { key: id })

definePageMeta({
    layout: 'games'
})
</script>

<style scoped></style>