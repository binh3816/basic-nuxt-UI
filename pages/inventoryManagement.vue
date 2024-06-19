<template>
    <div>
        <Header title="Inventory Management"></Header>
        <h3>Inventory Management</h3>
        <div>
            <h3>Products</h3>
            <table>
                <thead>
                    <tr>
                        <th>Product</th>
                        <th>Price</th>
                        <th>Quantity</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="product in products" :key="product.id">
                        <td>{{ product.name }}</td>
                        <td>{{ product.price }}</td>
                        <td>{{ product.quantity }}</td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
</template>

<script setup>
const products = [
    { id: 1, name: 'Product 1', price: 100, quantity: 5 },
    { id: 2, name: 'Product 2', price: 200, quantity: 10 },
    { id: 3, name: 'Product 3', price: 300, quantity: 0 },
]
</script>

<style lang="scss" scoped>

</style>
