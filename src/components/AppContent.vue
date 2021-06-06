<template>
     <div class="card card-w70">
      <h1>Резюме {{info.title}}</h1>
      <div class="avatar" v-if="info.avatar.length > 0">
        <img :src='info.avatar'>
      </div>
      <h2>{{info.subtitle}}</h2>
      <p>
        {{info.text}}
      </p>
      <h3>Добавьте первый блок, чтобы увидеть результат</h3>
      <button class="btn primary" @click="$emit('server')">Сохранить резюме</button>
    </div>
</template>


<script>
export default {
  props:['info'],
  emits:['server']
}
</script>

<style scoped>
    .avatar {
        width: 250px;
        height: 250px;
        border-right: 50%;
    }
    .avatar img {
        width: 100%;
        border-right: 50%;
    }
</style>