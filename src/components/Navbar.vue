<template>
    <nav id="nav">
        <router-link to="/" id="logo-url">
            <img :src="logo" :alt="alt" id="logo">
        </router-link>
        <router-link to="/"><span class="material-symbols-outlined">
                home
            </span>Home</router-link>
        <router-link to="/pedidos"><span class="material-symbols-outlined">
                fastfood
            </span>Pedidos</router-link>
    </nav>
</template>

<script>
export default {
    name: "Navbar",
    props: ["logo", "alt"]
}
</script>

<style scoped>
#nav {
    background-color: #222;
    border-bottom: 4px solid #111;
    padding: 15px 50px;
    display: flex;
    justify-content: flex-end;
    align-items: center;
}

#nav #logo-url {
    margin: auto;
    margin-left: 0;
}

#logo {
    width: 40px;
    height: 40px;
}

#nav a {
    color: #fcba03;
    text-decoration: none;
    margin: 12px;
    transition: .5s;
    display: f;
}

#nav a:hover {
    color: #fff;
}

@media (max-width: 600px) {
    #nav {
        position: fixed;
        width: 100%;
        bottom: 0;
        display: flex;
        justify-content: space-between;
    }

    #logo-url {
        display: none;
    }
}
</style>