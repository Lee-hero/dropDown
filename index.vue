// 折叠面板
<template>
    <!-- :class="isShow ? 'show-panel':'hide-panel'" -->
    <div class='drop-down' ref="dropWrap" :class="isShow ? 'show-panel':'hide-panel'">
        <div class="drop-box" ref="dropBox">
            <slot />
        </div>
        <span class="btn blueColor cursor-style" @click="operateFn" v-if="isDrop" v-text="isShow ? '收起':'展开'"></span>
    </div>
</template>

<script>
export default {
    data() {
        return {
            isShow: false,
            isDrop: false,
        }
    },
    methods: {
        operateFn() {
            this.isShow = !this.isShow;
        }
    },
    components: {

    },
    mounted() {
        let wrapHeight = this.$refs.dropWrap.offsetHeight;
        let boxHeight = this.$refs.dropBox.offsetHeight;
        console.log(wrapHeight, boxHeight)
        if (boxHeight > 50) {//限制高度50
            this.isShow = false;
            this.isDrop = true;
        } else {
            this.isDrop = false;
        }
    }
}
</script>

<style scoped lang='scss'>
.drop-down {
    width: 100%;
    .drop-box {
        width: calc(100% - 100px);
        display: inline-block;
    }
    .btn {
        margin-left: 20px;
        width: 80px;
        line-height: 32px;
        display: inline-block;
        vertical-align: top;
        font-size: 14px;
    }
}
.hide-panel {
    height: 50px;
    overflow: hidden;
}
</style>
