<template>
  <section class="">
    <div class="antialiased text-gray-900">
      <div
        class="px-4 py-10 mx-auto sm:px-6 sm:py-12 lg:max-w-4xl lg:py-16 lg:px-8 xl:max-w-7xl"
      >
        <article>
          <div class="mx-auto mb-10 text-left max-w-2xl md:max-w-4xl">
            <h1
          class="mb-4 text-4xl font-bold leading-tight text-gray-900 md:text-5xl capitalize text-center"
        >
          មេរៀន
        </h1>
            <div class="divider">Lesson Posts</div>


            <div class="pb-6 mb-6" v-for="article of articles" :key="article.slug">

              <nuxt-link :to="{ name: 'blog-slug', params: { slug: article.slug } }" class="flex flex-col items-center bg-white border rounded-lg shadow-md md:flex-row hover:bg-gray-100 dark:border-gray-700 dark:bg-gray-800 dark:hover:bg-gray-700">
                <!-- <a href="" > -->
                    <img class="object-cover w-full rounded-t-lg h-full md:h-auto md:w-48 md:rounded-none md:rounded-l-lg" :src="article.media" alt="">
                    <div class="flex flex-col justify-between p-4 leading-normal">
                        <h5 class="mb-2 text-2xl font-bold tracking-tight text-gray-900 dark:text-white">{{ article.title }}</h5>
                        <p class="mb-3 font-normal text-gray-700 dark:text-gray-400">{{ article.description }}</p>
                        <p class="text-base text-gray-500">
                          Posted: {{formatDate(article.createdAt)}}
                        </p>
                        <p class="text-base text-gray-500">
                          Updated: {{formatDate(article.updatedAt)}}
                        </p>
                    </div>
                <!-- </a> -->
              </nuxt-link>
            </div>

          </div>
        </article>
      </div>
    </div>


  </section>
</template>


<script>
// import HorizontalCard from "@/components/cards/horizontal-card.vue";
  export default {
    // components: { HorizontalCard },
    async asyncData({ $content, params }) {
      const pageNo = parseInt(params.number)
      const numArticles = 10

      const articles = await $content('articles')
        .where({ published: { $ne: true } })
        .limit(numArticles)
        .skip(numArticles * ( pageNo -1 ) )
        .only(['title', 'media', 'slug', 'createdAt', 'updatedAt', 'description'])
        .sortBy('createdAt', 'updatedAt', 'asc')
        .fetch()

        if(!articles.length)
          return error({ statusCode: 404, message: 'No articles found!' })

        const nextPage = articles.length === numArticles
        articles
        return{
          nextPage,
          articles,
          pageNo
        }
    },

    methods: {
      formatDate(date) {
        // format the date to be displayed in a readable format
        return new Date(date).toLocaleDateString('en', {year: 'numeric', month: 'long', day: 'numeric'})
        }
      },

  }
</script>
