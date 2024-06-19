<template>
    <v-layout class="rounded rounded-md">
        <v-navigation-drawer fixed app>
            <v-list-item title="My Application" subtitle="Vuetify"></v-list-item>
            <v-divider></v-divider>
            <v-list-item v-for="(link, index) in links" :key="index" :to="link.to" :title="link.title"></v-list-item>
            
        </v-navigation-drawer>
        <v-main class="d-flex align-center justify-center" style="min-height: 300px">
            <slot></slot>
        </v-main>
    </v-layout>
</template>
<script setup>
import { ref } from "vue";


const links = [
    { to: "/", title: "Homepage" },
    { to: "/userManagement", title: "User Management" },
    { to: "/storeManagement", title: "Store Management" },
    { to: "/priceManagement", title: "Price Management" },
    { to: "/vendorManagement", title: "Vendor Management" },
    { to: "/procurement", title: "Procurement" },
    { to: "/inventoryManagement", title: "Inventory Management" },
    { to: "/POS", title: "POS" },
];


</script>

