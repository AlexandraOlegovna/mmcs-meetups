<template>

  <div>
    <router-link v-if="link" :to="link" v-text="title"/>
    <span v-else v-text="title"/>

    <span v-text="fullDate" class="date"/>
  </div>

</template>

<script>
  export default {
    name: 'e-title',
    props: ['title', 'date', 'time', 'link', 'no-time'],
    computed: {
      fullDate() {
        const months = ['января', 'февраля', 'марта', 'апреля', 'мая', 'июня',
          'июля', 'августа', 'сентября', 'октября', 'ноября', 'декабря']

        let matched = /^(\d\d\d?\d?)[.|-](\d\d?)[.|-](\d\d?)$/.exec(this.date)
        if (!matched) return ''
        let [_, y, m, d] = matched

        let t = new Date()
        let isToday = (t.getFullYear() === +y) && (t.getMonth() === m - 1) && (t.getDate() === +d)

        let date = isToday ? 'сегодня в' : `${+d} ${months[m - 1]}`
        let time = `${this.noTime ? '' : this.time || ''}`

        return `${date} ${time}`
      }
    }
  }
</script>

<style scoped>
  div {
    font-size: 1.25em;
    font-weight: normal;
    font-family: 'Roboto Slab', serif;
  }

  a { color: #393939 }

  .date {
    font: 0.65em 'PT Sans';
    padding-left: 0.3em;
    color: #777;
    white-space: nowrap;
  }
</style>
