<template>
    <header class="header">
        <div class="header-top">
            <div class="header-top-left">
                <div class="header-top-search">
                    <img
                     src="/svg/header-search.svg" 
                     alt="search" 
                     class="header-top__icon">
                </div>
                <div class="header-top-mobile-menu" 
                @click="isOpenedMobileMenu = !isOpenedMobileMenu">
                    <img src="/svg/menu.svg" alt="menu" class="header-top__icon">
                </div>
            </div>
            <router-link to="/" class="header-logo">Avion</router-link>
            <div class="header-top-right">
                <div href="#" class="header-top-right__cart">
                    <router-link to="/cart">
                        <img src="/svg/header-cart.svg" alt="cart">
                        <span class="header-top-right__count" v-if="cartStore.cart.length">
                            {{cartStore.cart.length}}</span>
                    </router-link>
                </div>
                <div href="#" class="header-top-right__user">
                    <router-link to="/user">
                        <img src="/svg/header-user.svg" alt="user">
                    </router-link>
                </div>
            </div>
        </div>
        <div class="header-menu">
            <router-link
             class="haeder-menu__link"
             to="element.path" 
             v-for="(element, i) of menu"
             :key="i">{{element.name}}
            </router-link>
        </div>
        <div class="header-menu-mobile" v-if="isOpenedMobileMenu">
            <router-link
             class="haeder-menu-mobile__link"
             to="element.path" 
             v-for="(element, i) of menu"
             :key="i"
             >{{element.name}}</router-link>
        </div>

    </header>
</template>
<script setup>
import {ref} from 'vue'
import {useCartStore} from "@/store/cart.js";


const menu = [  
    {
        name: 'Plant pots',
        path: '/plant'

    },
    {
        name: 'Ceramics',
        path: '/ceramics'

    },
    {
        name: 'Tables',
        path: '/tables'

    }
]
const isOpenedMobileMenu = ref(false);
const cartStore = useCartStore();
</script>

<style lang="scss" scoped>
.header {
    height: 132px;
    background: #ffffff;
    @media screen and (max-width: 767px) {
    height: auto;
    }
    &-top {
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        height: 70px;
        align-items: center;
        border-bottom: 1px solid rgba(0, 0, 0, .1);
        margin: 0 28px;
        @media screen and (max-width: 767px) {
            margin: 0;
            border: none;
            height: auto;
            padding: 20px;
            display: flex;
            justify-content: space-between;
        }
        &__icon {
            display: block;
            margin-left: 16px;
        }
        &-left {
            display: flex;
            align-items: center;
            margin-left: 16px;
            @media screen and (max-width: 767px) {
                order: 2;
            }
        }


        &-right {
            display: flex;
            align-items: center;
            justify-content: flex-end;
            @media screen and (max-width: 767px) {
            display: none;
            }
        &__cart {
            margin-right: 16px;
            position: relative;
            }
        &__count {
            position: absolute;
            width: 15px;
            height: 15px;
            background: rgb(232, 1, 1);
            border-radius: 50%;
            color: #fff;
            font-size: 10px;
            text-decoration: none;
            display: flex;
            justify-content: center;
            align-items: center;
            left: -50%;
            bottom: 0;
            }
        }
    }
    &-logo {
        color: var(--dark-primary);
        font-size: 24px;
        text-decoration: none;
        font-family: var(--clash);
        text-align: center;
        &:hover {
            text-decoration: underline;
        }
    }

    &-menu {
        height: 62px;
        display: flex;
        justify-content: center;
        align-items: center;
            @media screen and (max-width: 767px) {
            display: none; 
            }
        * {
            margin: 0 22px;
            color: var(--primary);
            text-decoration: none;
            &:hover {
                text-decoration: underline;
            }
        }
        &-mobile {
            position: absolute;
            background: #fff;
            top: 60px;
            border: 1px solid;
            width: 90%;
            padding: 10px;
            text-align: center;
            * {
              display: block;
              margin-bottom: 20px;
              color: var(--gray);
              text-decoration: none;
              &:last-child {
                margin-bottom: 0;
              }
              &:hover {
                text-decoration: underline;
              }
            }
          }
  
        
    }
} 
</style>