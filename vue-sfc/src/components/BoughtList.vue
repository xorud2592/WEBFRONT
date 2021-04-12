<template>
    <div>
        <h2>산 물건들</h2>
        <ul>
            <li v-for="(item, index) in filterItems" v-bind:key="index">
                {{ item.name }}
                <button v-on:click="removeItem(item, index)">삭제</button>
                <button v-on:click="cancelBuy(item, index)">구매 취소</button>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    props: ['bought-items'],
    methods: {
        cancelBuy: function(item, index) {
            item.buy = false;
        },
        removeItem: function(item, index) {
            console.log("삭제할 항목:", item);
            //  삭제 이벤트발생
            this.$emit("remove-item", item);
        }
    },
    computed: {
        filterItems() {
            return this.boughtItems.filter(item => item.buy);
        }
    }
}
</script>