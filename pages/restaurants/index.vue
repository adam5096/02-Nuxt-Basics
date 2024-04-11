<template>
    <div>
        <Html :lang="dynamic > 50 ? 'en-GB' : 'en-US'">

        <Head>
            <Title>Top 50 restaurants in the world</Title>
            <Meta name="description" content="My page is cool">
            </Meta>
            <Link rel="preload" href="https://picsum.photos/200/300?random=2" as="script">
            </Link>
        </Head>

        </Html>
        <NuxtLayout name="custom">
            <div class="container">
                <RestaurantTable />
            </div>
        </NuxtLayout>
    </div>
</template>

<script setup lang="ts">
import { } from '#app'
</script>