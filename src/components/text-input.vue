<script>
    import {mapMutations} from 'vuex';

    export default {
        data() {
            return {
                content: ''
            };
        },
        methods: {
            onKeyup(e) {
                if (e.ctrlKey && e.keyCode === 13 && this.content.length) {
                    this.sendMessage(this.content);
                    this.content = '';
                }
            },
            // (...) 对象展开运算符
            ...mapMutations([
                'sendMessage'
            ])
        }
    };
</script>

<template>
    <div class="text">
        <textarea placeholder="按 Ctrl + Enter 发送" v-model="content" @keyup="onKeyup"></textarea>
    </div>
</template>

<style lang="less" scoped>
    .text {
        height: 160px;
        border-top: solid 1px #ddd;

        textarea {
            padding: 10px;
            height: 100%;
            width: 100%;
            border: none;
            outline: none;
            font-family: "Micrsofot Yahei";
            resize: none;
        }
    }
</style>