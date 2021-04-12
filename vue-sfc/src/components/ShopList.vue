<template>
    <div>
        <h2>살 물건들</h2>
        <ul>
            <li v-for='(item, index) in filterItems' v-bind:key="index" >
                {{ item.name }}
                <button v-on:click="buyItem(item, index)">구매</button>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    props: ['shopping-items'],
    methods: {
        buyItem: function(item, index) {
            console.log(item);
            item.buy = true;
        }
    },
    computed: {
        //  미리 리스트를 필터링
        filterItems() {
            return this.shoppingItems.filter(item => !item.buy);
        }
    }
}
</script>