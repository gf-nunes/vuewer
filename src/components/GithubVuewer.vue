<template>
  <v-container>
    <div><v-text-field label="Github apikey (opcional)" v-model="apikey"/></div>
    <GithubRepo @reposelected="onRepoSelected"/>
    <GithubIssues :repo="repo"/>
  </v-container>
</template>
  
<script>
  import GithubRepo from './GithubRepo';
  import GithubIssues from './GithubIssues';
  import {api} from '~api'
  export default {
    components: {
      GithubRepo,
      GithubIssues,
    },
    data: () => ({
      repo: null,
      apikey: '',
    }),
    methods: {
      onRepoSelected(repo){
        this.repo = repo
      },
    },
    watch: {
      apikey(){
        if (this.apikey) {
          api.set_apikey(this.apikey)
        }
      }
    }
  }
</script>
