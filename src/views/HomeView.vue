<template>
<div class="content-box">
    <h2>습관 기록</h2>
    <ul class="content-list">
        <li class="content-item" v-for="(item, index) in items" :item="item" :index="index" :key="item.id">
            <a v-on:click="goToDetail(item.item_id, $event)">{{item.title}}</a>
            <p class="start-date">{{item.start_date}}</p>
        </li>
    </ul> 
    <router-link to="/write" class="btn-primary">습관 등록하기</router-link>
</div>
</template>

<script>
export default { 
    data() {
        return {
            title:'title',
            items: [
                { 
                    title: '스트레칭 하기',
                    start_date: '2022.03.20',
                    item_id: '1'
                },
                { 
                    title: '물 2L 마시기',
                    start_date: '2022.03.18',
                    item_id: '2'
                },
            ],
        };
    },
    methods: {
        goToDetail(item_id) {
            console.log(item_id);
            // this.$router.push({path:'/detail', query:{id:item_id}});
            this.$router.push('/detail/'+item_id)
        }
    }
}
</script>