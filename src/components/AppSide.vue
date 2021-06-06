<template>
    <form class="card card-w30">
        <div class="form-control">
        <label for="type">Тип блока</label>
        <select id="type" v-model="selectTheme">
            <option value="title">Заголовок</option>
            <option value="subtitle">Подзаголовок</option>
            <option value="avatar">Аватар</option>
            <option value="text">Текст</option>
        </select>
        </div>

        <div class="form-control">
        <label for="value">Значение</label>
        <textarea v-model.trim="value" id="value" rows="3"></textarea>
        </div>

        <button @click.prevent="$emit('addInfo',selectTheme,value)" :disabled='value.length < 3' class="btn primary">Добавить</button>
    </form>
</template>

<script>
export default {
data() {
    return {
        selectTheme: 'title',
        value: ''
    }
},
emits:['addInfo']
}
</script>