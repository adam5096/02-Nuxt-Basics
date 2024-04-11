<template>
    <div>
        <slot name="header"></slot>
        <div>
            <img src="https://picsum.photos/100/100?random=1">
        </div>
    </div>
    <slot name="redirectEl"></slot>
</template>

<style scoped>
img {
    width: 10rem;
}
</style>