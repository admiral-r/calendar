<template>
    <div>
        <div class="d-flex justify-content-center align-items-center p-4">
            <div class="pointer">
                <previousMonth @click="previousMonth"></previousMonth>
            </div>
            <div class="month-title user-select-none mb-0">
                <span class="h6">{{year}} - </span>
                <span class="h6">{{months[month]}}</span>
            </div>
            <div class="pointer">
                <nextMonth @click="nextMonth"></nextMonth>
            </div>
        </div>
        <div class="calendar-content">
            <week :item="item" v-for="(item , index) in weekData" :key="index"></week>
        </div>
        <hr>
        <div class="calendar-content">
            <days :date="item.date" :day="item.day" v-for="(item , index) in daysData" :key="index"></days>
        </div>
    </div>
</template>
<script scoped>
import week from './week.vue'
import days from './days.vue'
import nextMonth from './nextMonth.vue'
import previousMonth from './previousMonth.vue'
export default {
    name: 'month',
    components: { days, week, nextMonth, previousMonth },
    props: {
    },
    data() {
        return {
            weekData: [
                { title: 'Sun'},
                { title: 'Mon' },
                { title: 'Tue' },
                { title: 'Wed' },
                { title: 'Thu' },
                { title: 'Fri' },
                { title: 'Sat'},
            ],
            daysData: [],
            day: new Date().getUTCDate(),
            months: ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"],
            month: new Date().getMonth(),
            year: new Date().getFullYear(),
        }
    },
    methods: {
        createMonth(year, month) {
            let time = new Date(year, month, 1)
            for (let i = 0; i < time.getDay(); i++) {
                this.daysData.push(
                    {
                        date: null,
                        day: this.day
                    },
                )
            }
            while (time.getMonth() === month) {
                this.daysData.push(
                    {
                        date: new Date(time),
                        day: this.day
                    },
                );
                time.setDate(time.getDate() + 1);
            }
        },
        nextMonth() {
            this.daysData = []
            if (this.month + 1 === 12) {
                this.year += 1
                this.month = 0
            }
            else {
                this.month += 1
            }
            this.createMonth(this.year, this.month)
        },
        previousMonth() {
            this.daysData = []
            if (this.month - 1 === -1) {
                this.year -= 1
                this.month = 11
            }
            else {
                this.month -= 1
            }
            this.createMonth(this.year, this.month)
        },
    },
    mounted() {
        this.createMonth(this.year, this.month)
    }
}
</script>
  
<style scoped>
.calendar-content {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    flex: 1 1 100%;
}

.month-title {
    width: 10rem;
}
</style>