<script setup>
    import BarItems from './Components/ItemsContainer/BarItems.vue';
    import Item from "./Components/Item/Item.vue";
    import Total from './Components/Total/Total.vue';
    import CurrencyInput from './Components/CurrencyInput/CurrencyInput.vue'
    import { useCurrencyInput } from 'vue-currency-input';
    import { ref } from 'vue';

    const CurrencyInputClear = useCurrencyInput({
     locale: 'pt-BR',
     currency: 'BRL',
     precision: 2,
    });


    //Variaveis
    const products = ref([]); // Lista
    let id = 0;
    const product = ref(''); const quantity = ref(0); const price = ref(0); const subtotal = ref(0); const total = ref(0);  const currencyInputRef = ref(null);
    
    function AddProduct() {
        subtotal.value = (quantity.value * price.value).toFixed(2); // Limitando subtotal a 2 casas decimais
        total.value = (parseFloat(total.value) + parseFloat(subtotal.value)).toFixed(2);
        products.value.push({id: id++, product: product.value, quantity: quantity.value, price: price.value, subtotal: subtotal.value, total:  total.value})
        product.value = ''; quantity.value = 0; price.value = 0; subtotal.value = 0;
        CurrencyInputClear.setValue(0);
    }

</script>

<template>
 <main class="font-saira font-medium">
        <div class="mr-6 ml-6 mt-2 ">
            <form @submit.prevent='AddProduct'>
                <input type="text" v-model="product" required placeholder="Produto" class="w-96 h-10 rounded-md">
                <div class="flex flex-row mt-5">
                    <input type="number" v-model="quantity" required placeholder="Quantidade" class="w-40 h-10 rounded-md">
                    <CurrencyInput 
                    @change="v => price = v"
                    :custom-instance="CurrencyInputClear"
                    class = " ml-8 w-40 h-10 rounded-md"
                    />
                </div>
                <div class="mt-4 flex justify-end">
                    <button type="submit" class="w-24 h-9 rounded-md font-semibold text-xl bg-white">Inserir</button>
                </div>
            </form>
            <div class="mt-4 h-[600px] rounded-md bg-zinc-800">
                <BarItems/>
                <Item  :products="products" />
            </div>
            <div class="mt-3 flex justify-end">
                <Total :total="total"/>
            </div>
        </div>
    </main>
</template>