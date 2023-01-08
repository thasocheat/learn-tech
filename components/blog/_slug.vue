<template>
  <prev-next :prev="prev" :next="next"></prev-next>
</template>

<script>
  export default {
    async asyncData({ $content, params }) {
      //Here, this will fetch the article from the article/ folder
      //based on the name provided in the 'params.slug`
      const article = await $content('articles', params.slug).fetch()


        // assign the first two objects in returned array to prev & next constant variables
      const [prev, next] = await $content('articles')
        // fetch only the title and slug from the articles
        .only(['title', 'slug', 'updatedAt'])
        // sortby time updated, in ascending order
        .sortBy('updatedAt', 'asc')
        // get the correct slug
        .surround(params.slug)
        // fetch data
        .fetch()

      // return the data to be vailable for use in the file
      return { article, prev, next }
    },

  }

</script>

