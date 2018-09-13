<template>

    <div v-if="question">
        <edit-question :question = question v-if="editing"></edit-question>
        <show-question :question = question v-else></show-question>  
    </div>
  
</template>

<script>
  import showQuestion from './showQuestion'
  import EditQuestion from './EditQuestion'
	export default{

    components:{showQuestion,EditQuestion},
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