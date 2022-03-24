<template>
    <div class="content-box">
        <h2>습관 추가하기</h2>
        <input type="text" name="" v-model="itemTitle">
        <button type="button" class="btn btn-primary" v-on:click="addList">추가</button>
    </div>
</template>

<script>
export default { 
    methods: {
        addList: function() {
            console.log('addList');
            this.items.push({
                title: this.itemTitle
            })
        }
    }
}
</script>