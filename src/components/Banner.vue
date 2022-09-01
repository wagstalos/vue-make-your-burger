<template>
    <div id="main-banner">
        <h1>Make you Burger</h1>
        <p>formulário</p>
    </div>
</template>

<script>

export default{
    name: "Banner",

}

</script>

<style scoped>
    #main-banner{
        background-image: url('../assets/burger.jpg');
        background-position: 0 -250px;
        background-size: cover;
        height: 500px;
        display: flex;
        align-items: center;
        justify-content:  flex-start;
    }

    #main-banner h1{
        color: #fff;
        text-align: center;
        font-size: 60px;
        background-color: #222;
        padding: 20px 40px;
    }
</style>