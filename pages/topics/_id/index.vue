<templete>
    <div class="container">
        <h2>Single topic page</h2>
        <div class="bg-light mt-5 mb-5" style="padding: 20px;">
            <h2 class="display-3">{{topic.title}}</h2>
            <hr>
            <p class="text-muted">{{topic.created_at}} by {{topic.user.name}}</p>

            <div v-for="(content,index) in topic.post" :key="index" class="ml-5 content">
                {{content.body}}
                <p class="text-muted">{{content.created_at}} by {{content.user.name}}</p>

            </div>
        </div>
    </div>
</templete>
<script>
  export default {
    data() {
      return {
        topic: ''
      }
    },
    async asyncData({ $axios, params }) {
      const { data } = await $axios.$get(`/topics/${params.id}`)
      return {
        topic: data
      }
    }
  }
</script>