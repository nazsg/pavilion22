<template>
  <div class="setmenus">
    <!-- <div class="bg"></div> -->
    <div class="page_container">
      <table4Col2prices
        title="Lunch Menus"
        :menus="all_menus.filter((m) => m.category == 'lunch_menus')"
      />

      <table2Col
        title="Choose Any One Of The Following Starter Dishes As A 2-course Lunch"
        :menus="all_menus.filter((m) => m.category == 'choices')"
      />

      <table3Col
        title="Set Menu"
        :menus="all_menus.filter((m) => m.category == 'set_menu')"
      />
      <our-clause />
    </div>
  </div>
</template>

<script>
export default {
  head: {
    title: 'Set Menus | Bangkok Pavilion',
    meta: [
      { name: 'viewport', content: 'width=device-width, initial-scale=1' },
      {
        hid: 'description',
        name: 'description',
        content: 'Our set menus - Menu A, Menu B, Menu C, Menu D, Menu E',
      },
    ],
  },
  data() {
    return {
      all_menus: [],
    }
  },
  created() {
    this.$axios.get('all_menus?menu=set_and_lunch').then((res) => {
      this.all_menus = res.data
    })
  }, // TABLE:
  // asyncData(context) {
  //   return context.$axios
  //     .get('all_menus?menu=set_and_lunch')
  //     .then((res) => {
  //       return { all_menus: res.data }
  //     })
  //     .catch((error) => {
  //       context.error({
  //         message: 'ajax problem', // if custom error set
  //       })
  //       // context.redirect('/')
  //     })
  // },
}
</script>
