<template>
    <div class="content-box">
        <div v-for="(item, index) in items" v-bind:item="item" v-bind:index="index" v-bind:key="item.id">
            <div v-if="item.item_id == $route.params.id">
                <h2>{{item.title}}</h2>
                <p>시작 날짜 {{item.start_date}}</p>
                <v-calendar class="custom-calendar max-w-full" :attributes="attributes" disable-page-swipe is-expanded>
                    <div slot="day-content" @click="dayClick" slot-scope="{ day, attributes }" class="day-content">
                        <!-- <div class="day-circle" v-for="(attr, index) in attributes" :index="index" :key="attr.id" :class="attr.status">{{attr.status}}</div> -->
                        <div class="day-circle" v-for="attr in attributes" :key="attr.key" :class="attr.customData.status" :id="'circle-'+attr.key"></div>
                        <span class="day-label">{{ day.day }}</span>
                    </div>
                </v-calendar>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        var now = new Date();
        var month = now.getMonth();
        var year = now.getFullYear();
        var day = now.getDate();
        return {
            date: new Date(),
            today: new Date(year, month, day) * 1,
        // masks: {
        //     weekdays: "WWW"
        // },
            attributes: [
                {
                    key: 1,
                    customData: {
                        title: '타이틀',
                        status: 'on',
                    },
                    dates: new Date(year, month, 1)
                },
                {
                    key: 4,
                    customData: {
                        title: '타이틀',
                        status: 'on',
                    },
                    dates: new Date(year, month, 4)
                },
            ],
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
        dayClick(event) {
            var target = event.target;
            console.log(target);
            console.log(target.closest('.day-circle'));
            if(target.closest('.day-content .day-circle') !== null) {
                target.closest('.day-content .day-circle').classList.remove('on');
            } else {
                var circle = document.createElement('div');
                circle.setAttribute('class', 'day-circle on');
                target.closest('.day-content').prepend(circle);
            }
        }
    }
};
</script>