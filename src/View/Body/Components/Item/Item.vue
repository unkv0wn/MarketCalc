<!-- BarItems.vue -->
<template>
    <main>
        <div v-for="product in products" :key="product.id" class="bg-gray-300 opacity-35 w-auto text-base h-8 flex flex-row justify-start items-center font-bold">
            <div class="basis-10/12 ml-1">{{ product.product }}</div>|
            <div class="basis-1/3 flex justify-center">{{ product.quantity }}</div>|
            <div class="basis-1/4 flex justify-center">{{ product.price }}</div>|
            <div class="basis-1/3 flex justify-center">{{ product.subtotal }}</div>
        </div>
    </main>
</template>

<script>

export default {
    props: {
        products: Array // Definindo as props do componente
    }
}
</script>