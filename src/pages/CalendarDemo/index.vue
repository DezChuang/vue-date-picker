<script>
  import Calendar from '@/components/Calendar'
  export default {
    name: 'CalendarDemo',
    components: {
      Calendar
    },
    data() {
      return {
        selectedDate: null
      }
    },
    computed: {
      dateText() {
        const { year, month, day } = this.selectedDate
        const zMonth = ('0' + (month + 1)).slice(-2)
        const zDay = ('0' + day).slice(-2)
        return `${year}-${zMonth}-${zDay}`
      }
    },
    methods: {
      onSelect(date) {
        this.selectedDate = date
      }
    },
    beforeMount() {
      const now = new Date().toISOString()
      const currentDate = {
        year: parseInt(now.slice(0, 4)),
        month: parseInt(now.slice(5, 7)) - 1,
        day: parseInt(now.slice(8, 10))
      }
      this.selectedDate = JSON.parse(JSON.stringify(currentDate))
    }
  }
</script>

<template src="./template.html" />
<style lang="scss" src="./style.scss" scoped />
