<template>
  <v-container fluid>
    <v-form @submit.prevent="update">
      <v-text-field
        v-model="form.title"
        label="Title"
        type="text"
        required
      ></v-text-field>

      <markdown-editor v-model="form.body"></markdown-editor>

      <v-card-actions>
        <v-btn icon small type="submit">
          <v-icon color="teal">save</v-icon>
        </v-btn>

      <v-btn icon small @click="cancel">
        <v-icon color="red">cancel</v-icon>
      </v-btn>

      </v-card-actions>
    </v-form>

  </v-container>
</template>

<script>
	export default{
    props:['question'],
    data(){
      return{
        form:{
          title:null,
          body:null,
        },
      }
    },
    methods:{
      cancel(){
        EventBus.$emit('cancelEditing')
      },
      update(){
        axios.patch(`/api/question/${this.form.slug}`,this.form)
        .then(res => this.cancel())
      }
    },
    mounted(){
      this.form = this.question
    }
	}
</script>

<style>
	
</style>