<template>
    <div class="container column">
      <AppSide @addInfo='addInfo'/>
      <AppContent :info='info' @server='addServerInfo'/>
    </div>
  <div class="container">
    <p>
      <button class="btn primary" @click="load">Загрузить резюме</button>
    </p>
      <app-list-resume 
      v-for="r in serverInfo"
      :key="r.id"
      :resume='r'
      ></app-list-resume>
    </div>
</template>

<script>
import AppSide from './components/AppSide.vue'
import AppContent from './components/AppContent.vue'
import AppListResume from './components/AppListResume.vue'
import axios from 'axios'
export default {
  name: 'App',
  components: {AppSide,AppContent,AppListResume},
  data() {
    return {
      value: '',
      info: {
            title: '',
            subtitle: '',
            avatar: '',
            text: ''
        },
      serverInfo: []
    }
  },
  methods: {
    addInfo(select,value) {
      this.info[select] = value 

    },
    async addServerInfo() {
        const res = await fetch('https://vur-resume-default-rtdb.firebaseio.com/resune.json',{
            method: 'POST',
            headers: {
                'Content-type': 'application/json'
            },
            body: JSON.stringify(this.info)
        })
        const fir = await res
        this.serverInfo.push({
          id: fir,
          ...this.info

        })
    },
    async load () {
      const {data} = await axios.get('https://vur-resume-default-rtdb.firebaseio.com/resune.json')
      this.serverInfo = Object.keys(data).map( key => {
        return {
          id: key,
          ...data[key]
        }
      })
      console.log(this.serverInfo);
    }

  },
}
</script>
<style>

</style>
