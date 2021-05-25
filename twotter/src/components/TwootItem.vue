<template>
    <div class="twoot-item" @click="favouriteTwoot(twoot.id)"> 
        <div class="user-profile__twoot">
            <div class="user-profile__user">@{{username}}: </div>
            <div class="user-profile__twoot-content">{{twoot.content}}</div>
        </div>
    </div>
</template>

<script>
export default {
    name: "TwootItem",
    props: {
        username: {
            type: String,
            required: true
        },
        twoot: {
            type: Object,
            required: true
        }
    },
    methods: {
    favouriteTwoot(id) {
        this.$emit("favourite", id)
    }
}


}
</script>

<style scoped>
.twoot-item{background:white; border-width: 1px; border-color: black; border-style:solid; border-radius:5px; margin-bottom:5px;}
.twoot-item:hover{transform:scale(1.1,1.1);cursor:pointer;}
.user-profile__user{display:inline;font-weight:bold;}

.user-profile__twoot-content{display:inline;}
</style>