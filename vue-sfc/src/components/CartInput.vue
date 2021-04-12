<template>
    <div>
        <p>{{ message }}</p>
        <input v-model="newItem"><button v-on:click="addItem">추가</button>
    </div>
</template>

<script>
export default {
    data: function() {
        return {
            message: "상품을 입력하세요",        
            newItem: ""    //  새로 살 물건 이름
        }
    },
    watch: {
        //  모델의 변경을 적극적으로 감시
        newItem: function(item) {
            console.log("item:", item);
            if (item.trim().length > 0) {
                this.message = "상품을 등록하실 수 있습니다";
            } else {
                this.message = "상품을 입력하세요";
            }
        }
    },
    methods: {
        addItem: function() {
            console.log("새로살 물건:", this.newItem);
            //  입력된 값 체크
            if (this.newItem.trim().length > 0) {
                //  추가할 수 있다.
                //  부모에게 이벤트를 던져주자
                this.$emit("add-item", this.newItem);
                this.newItem = "";
            }
        }
    }
}
</script>