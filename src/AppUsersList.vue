<template>
    <div class="usersList" v-if="users.length != 0">
        <span class="listItem" v-for="(item, key) in users" :key="key">{{ `${key}: ${item.userName}` }}</span>
    </div>
    <div class="usersList" v-else>
        <span>Людей нет.</span>
        <button class="btn accept" @click="$emit('loadUsers')">Загрузить людей</button>
    </div>
</template>

<script>
export default ({
    props:{
        users: {
            type: Object,
            required: false,
            default: [],
        }
    },
    emits: ['loadUsers'],
})
</script>
