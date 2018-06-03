<template>
<div>
  <home-calendar
    ref="HomeCalendar"
    :markDateMore="arr"
    v-on:choseDay="clickDay"
    v-on:changeMonth="changeDate"
    agoDayHide='1517483961'
    futureDayHide='1536054400'
  ></home-calendar>
</div>
</template>

<script>
import HomeCalendar from './components/Calendar'
export default {
  name: 'Home',
  components: {
    HomeCalendar
  },
  data () {
    return {
      arr: [{
        date: '2018-4-1',
        className: 'mark1'
      }, {
        date: '2018-4-2',
        className: 'mark1'
      }, {
        date: '2018-4-13',
        className: 'mark2'
      }]
    }
  },
  methods: {
    clickDay (data) {
      console.log('选中了', data) // 选中某天
      // this.$toast('选中了' + data)
    },
    clickToday (data) {
      console.log('跳到了本月', data) // 跳到了本月
    },
    changeDate (data) {
      // this.$toast('切换到的月份为' + data)
      console.log('左右点击切换月份', data) // 左右点击切换月份
    },
    demo () {
      // this.$refs.Calendar.ChoseMonth('2017-12-12',false); // 跳到12月12日 但是不选中12月12日
      this.$refs.Calendar.ChoseMonth('2017-12-12') // 跳到12月12日
    }
  },
  created () {
    function format (date, index) {
      date = new Date(date)
      return `${date.getFullYear()}-${date.getMonth() + 1}-${index}`
    }
    this.arr = [{
      date: format(new Date(), 1),
      className: 'mark1'
    }, {
      date: format(new Date(), 2),
      className: 'mark1'
    }, {
      date: format(new Date(), 13),
      className: 'mark2'
    }]
  }
}
</script>

<style lang="css" >
.mark1 {
    background-color: red;
}

.mark2 {
    background-color: blue;
}
</style>
