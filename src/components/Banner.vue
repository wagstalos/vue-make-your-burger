<template>
    <div id="main-banner">
        <h1 class="color-yellow"> Make you BURGER</h1>
    </div>
</template>

<script>

export default {
    name: "Banner",
}

</script>

<style scoped>
#main-banner {
    background-image: url('../assets/burger.jpg');
    background-position: 0 -350px;
    background-size: cover;
    height: 380px;
    display: flex;
    align-items: center;
    justify-content: flex-start;
}

#main-banner span {
    color: red;
}

#main-banner h1 {
    text-align: center;
    font-size: 60px;
    background-color: rgba(0, 0, 0, .5);
    padding: 20px 40px;
    font-weight: 700;
    /* -webkit-text-stroke-width: 1px;
    -webkit-text-stroke-color: #fff;
    color: transparent;
    line-height: 60px; */
}

.color-yellow {
    background: -webkit-linear-gradient(rgb(243, 135, 4), rgb(255, 239, 12));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
}

@media (max-width: 600px) {
    #main-banner {
        height: 350px;
    }
}
</style>