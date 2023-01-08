<template>
  <div class="antialiased text-gray-900">
    <div
      class="px-4 py-10 max-w-3xl mx-auto sm:px-6 sm:py-12 lg:max-w-4xl lg:py-16 lg:px-8 xl:max-w-7xl"
    >
      <article>
        <h1 class="sr-only">{{ article.title }}</h1>
        <div class="mx-auto mb-10 text-left max-w-2xl md:max-w-4xl">
          <div class="pb-6 mb-6 border-b border-gray-200">
            <h1
              class="mb-3 text-2xl font-bold leading-relaxed text-left text-gray-900 md:leading-tight md:text-4xl capitalize"
              itemprop="headline"
            >
              {{ article.title }}
            </h1>
            <p class="text-base text-gray-500">
              Posted: {{formatDate(article.createdAt)}} / {{ article.by }}
            </p>
          </div>

          <img
            :src="article.media"
            class="object-cover w-full h-64 bg-center rounded"
          />
          <!-- this is where we will render the article contents -->
          <nuxt-content :document="article" />

          <div>
            <prevnext-prev-next :prev="prev" :next="next"></prevnext-prev-next>
          </div>
        </div>
      </article>
    </div>
  </div>
</template>

<script>
import { async } from 'q';

  export default {
    async asyncData({ $content, params }) {
      //Here, this will fetch the article from the article/ folder
      //based on the name provided in the 'params.slug`
      const article = await $content('articles', params.slug).fetch()


        // assign the first two objects in returned array to prev & next constant variables
      const [prev, next] = await $content('articles')
        // fetch only the title and slug from the articles
        .only(['title', 'media', 'slug', 'createdAt', 'updatedAt'])
        // sortby time updated, in ascending order
        .sortBy('createdAt', 'updatedAt', 'asc')
        // get the correct slug
        .surround(params.slug)
        // fetch data
        .fetch()

      // return the data to be vailable for use in the file
      return { article, prev, next }
    },
    methods: {
        // format the date to be displayed in a readable format
        formatDate(date){
            return new Date(date).toLocaleDateString('en', {year: 'numeric', month: 'long', day: 'numeric'})
        }
    }
  }

</script>
<style scoped>
/* @layer components { */
  .article {
      @apply prose lg:prose-xl;
      @apply p-4 mt-6 lg:mt-8 m-auto lg:max-w-3xl;
  }

  .article-header{
      @apply mb-12 pb-8 lg:mb-16 border-gray-200 border-b-2;
  }

  .article-header h1{
      @apply mb-0;
  }

  .article-header .details-cont span{
      @apply text-opacity-50 text-sm;
  }
/* } */
</style>
