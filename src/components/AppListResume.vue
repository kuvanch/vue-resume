<template>
    <div class="card">
      <h2>{{resume.title}}</h2>
      <ul class="list">
        <li class="list-item">
            <div class="avatar">
                <img :src='resume.avatar'>
            </div>
          <div>
            <h2>{{resume.subtitle}}</h2>
            <p>{{resume.text}}</p>
          </div>
        </li>
      </ul>
    </div>
</template>

<script>
export default {
    props:['resume']
}
</script>

<style scoped>
    .list-item {
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .avatar img {
        width: 200px;
        height: 200px;
        padding-right: 20px;
    }
    h2 {
        margin: 0;
    }
</style>