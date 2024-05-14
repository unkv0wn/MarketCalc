<script>
import { CurrencyDisplay } from 'vue-currency-input';

    export default {
        props: {
            total: Number.toString()
        }
    }

</script>

<template>
    <div class="h-[40px] w-[200px] bg-white rounded-md flex flex-row items-center">
        <div class="basis-1/2">
            <h2 class="font-saira text-xl font-medium ml-1">Total :</h2>
        </div>
        <div class="basis-1/2 ">
            <h2 class="font-saira text-2xl font-medium">{{ total }}R$</h2>
        </div>
    </div>
</template>


