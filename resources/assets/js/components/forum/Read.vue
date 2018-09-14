<template>

    <div v-if="question">
        <edit-question :question = question v-if="editing"></edit-question>
        <show-question :question = question v-else></show-question>  
        <v-container>
          <replies :question="question"></replies>
          <new-reply :questionSlug="question.slug"></new-reply>
        </v-container>
    </div>
  
</template>

<script>
  import showQuestion from './showQuestion'
  import EditQuestion from './EditQuestion'
  import Replies from '../reply/replies'
  import NewReply from '../reply/newReply'

	export default{

    components:{showQuestion,EditQuestion,Replies,NewReply},
    data(){
      return{
        question:null,
        editing:false
      }
    },
		created(){
        this.listen()
        this.getQuestion()
    },
    methods:{
      listen(){
        EventBus.$on('startEditing',()=>{
          this.editing = true
        })
        EventBus.$on('cancelEditing',()=>{
          this.editing = false
        })
      },
      getQuestion(){
        axios.get(`/api/question/${this.$route.params.slug}`)
        .then(res => this.question = res.data.data)
      }
    }
	}
</script>

<style>
	
</style>