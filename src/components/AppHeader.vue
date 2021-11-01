<template>
    <div class="Header-container">
        <div class="logo-container">
            <router-link to="/"><img src="../assets/logo.svg" alt="LOGO" class="logo"></router-link>
        </div>
        <div class="nav-bar">
            <ul class="navBar">
                <li>
                    <router-link to="/" >Home</router-link>
                </li>
                <li>
                    <router-link to="/about" exact >About</router-link>
                </li>
                <li>
                    <router-link to="/portfolio" exact >Portfolio</router-link>
                </li>
                <li>
                    <router-link to="/contact" exact >Contact</router-link>
                </li>
            </ul>

        </div>
    </div>
</template>

<style scoped>
    .Header-container {
        background: #B0E0E6;
        height: 80px;
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 0 15px;
    }
    .logo {
        width: 55px;
    }
    .navBar{
        list-style-type: none;
        display: flex;
        align-items: center;
    }
    .navBar > li {
        font-size: 20px;
        margin-right: 20px;
    }
    .navBar > li > a {
        text-decoration: none;
        color: #3867aa;
        transition: 0.7s;
    }
    .navBar > li > a.router-link-active,
    .navBar > li > a:hover {
        color: #ff0000;
    }
</style>

