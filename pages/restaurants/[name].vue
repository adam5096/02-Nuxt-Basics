<script setup lang="ts">
import restaurants from '@/data.json'//匯入資料集並取名restaurants
const route = useRoute();//取得路由實例
//當用戶點擊餐廳排名單上餐廳時會跳轉對應餐廳頁面
// 取得對應餐廳頁面Url的params.name位置的參數
const name = route.params.name
// 從資料集data.json中逐筆比對，當資料集中餐廳名稱r.name等於用戶點擊的餐廳名稱name時(透過路由實例方法取得)
// 將比對符合的r.name都撈取出來存放在restaurant中
const restaurant = restaurants.find((r) => r.name === name)

useSeoMeta({
    title: (restaurant as any).value ? name : "404 - Restaurant not found",
    meta: [
        {
            name: "viewport",
            conotent:"width=device-width"
        }
    ]
})
</script>

<template>
    <div>
        <!-- 採用custom.vue所設置樣式 -->
        <NuxtLayout name="custom" v-if="restaurant">
            <div class="restaurant-container">
                <div class="image-container">
                    <img :src="restaurant?.imageUrl" alt="">
                </div>
                <div class="info-container">
                    <h1>{{ restaurant?.name }}</h1>
                    <div class="stats-container">
                        <h5>Revenue (in billions)</h5>
                        <p>${{ restaurant?.revenue }}</p>
                    </div>
                    <div class="stats-container">
                        <h5>Number of Stores</h5>
                        <p>{{ restaurant?.numberOfStores }}</p>
                    </div>
                    <p class="content">{{ restaurant?.content }}</p>
                </div>
            </div>
        </NuxtLayout>
        <div class="restaurant-not-found" v-else>
            <!-- 採用error.vue所設置樣式 -->
            <NuxtLayout name="error">
                <template #header>
                    <h1>Restaurant not found</h1>
                </template>

                <template #redirectEl>
                    <NuxtLink to="/">Go Back</NuxtLink>
                    <button class="btn btn-primary btn-lg" @click="$router.push('/restaurants')">Go Back</button>
                </template>
            </NuxtLayout>
        </div>
    </div>
</template>

<style scoped>
.restaurant-container {
    display: flex;
}

.image-container {
    width: 75%;
    height: 95vh;
}

.image-container img {
    width: 100%;
    height: 100%;
}

.restaurant-not-found {
    height: 75vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
}

.info-container {
    padding: 3rem;
    width: 50%;
}

.info-container h1 {
    text-transform: uppercase;
    font-size: 6rem;
    margin-bottom: 1rem;
}

.stats-container {
    display: flex;
    align-items: flex-end;
    margin-bottom: 1rem;
}

.stats-container h5 {
    width: 20rem;
    font-size: 2rem;
    margin: 0;
    margin-right: 5rem;
}

.stats-container p {
    font-size: 2rem;
    margin: 0;
}

.content {
    font-size: 1.5rem;
    margin-top: 4rem;
}

img {
    width: 10rem;
}
</style>