<script setup>
import { RouterLink } from 'vue-router';
</script>

<template>
    <header>
        <nav class="container">
            <div class="branding">
                <img src="../assets/image.png" alt="">
                <h1>قائمة مهام</h1>
            </div>
            <ul class="nav-routes">
                <RouterLink to="/"> الرئيسية </RouterLink>
                <RouterLink to="/about">حول</RouterLink>
            </ul>
        </nav>
    </header>
</template>



<style lang="scss" scoped>
header {
    background-color: #f1f1f1;

    nav {
        display: flex;
        align-items: center;
        padding: 10px 36px;

        .branding {
            display: flex;
            align-items: center;
            gap: 2px;

            img {
                max-width: 50px;
            }

            h1 {
                font-size: 24px;
            }
        }

        .nav-routes {
            display: flex;
            flex: 1;
            justify-content: flex-end;
            gap: 12px;
            list-style: none;

            a {
                text-decoration: none;
                color: inherit;
            }
        }
    }
}
</style>