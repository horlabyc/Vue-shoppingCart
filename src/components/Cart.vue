<template>
    
    <div>
        <h2 class="text-center">Your Cart</h2>
        <ul class="list-group">
            <li class="list-group-item" :key="item.id" v-for="item in items">
                {{item.title}} - ${{item.price}}
                <button @click="$emit('remove-from-cart', item)" class="btn badge badge-danger float-right">
                    Remove From Cart
                </button>
            </li>
        </ul>

        <div class="card p-3 my-5">
            <h4 class="text-center">${{ total }}</h4>
        </div>

        <button @click="$emit('pay')" :disabled="items.length === 0" class="btn btn-info form-control">
            Pay Now
        </button>
    </div>



</template>

<script>
export default {
    props: ['items'],

    computed: {
        total() {
            return this.items.reduce((acc, item) => acc + Number(item.price), 0);
        }
    }
}
</script>
