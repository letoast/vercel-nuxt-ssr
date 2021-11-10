<template>
  <img :src="dog.image" alt="">
</template>

<script>
export default {
  data () {
    return {
      dog: {
        image: ''
      }
    }
  },
  async fetch () {
    const { data } = await this.$axios.get('https://dog.ceo/api/breeds/image/random')
    this.dog.image = data.message
  },
  head () {
    return {
      title: this.dog.image,
      meta: [
        {
          hid: 'og:title',
          name: 'og:title',
          content: this.dog.image
        },
        {
          hid: 'og:image',
          name: 'og:image',
          content: this.dog.image
        }
      ]
    }
  }
}
</script>
