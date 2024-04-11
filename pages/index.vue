<template>
    <div>
        <Html :lang="dynamic > 50 ? 'en-GB' : 'en-US'">
        <Head>
            <Title>Restaurantly</Title>
            <Meta name="description" content="My page is cool"></Meta>
            <Link rel="preload" href="https://picsum.photos/200/300?random=2" as="script"></Link>
        </Head>
        </Html>
        <div class="container">
            <h1>Welcome to Restaurantly</h1>
            <NuxtLink to="/restaurants">Go to restaurants</NuxtLink>
        </div>
    </div>
</template>

<style scoped>
.container {
    text-align: center;
    margin-top: 5rem;
}
</style>