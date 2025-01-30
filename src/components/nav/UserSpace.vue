<template>
    <div>
        <slot>
            <small @click="isOpen = true" style="cursor: pointer">
                ⛏关于
            </small>
        </slot>
    </div>

    <teleport to="body">
        <transition name="fade">
            <div class="popup" v-if="isOpen">
                <div class="flex">
                    <strong>关于</strong>
                    <span class="close" @click="isOpen = false"> [关闭] </span>
                </div>
                <p><strong>警告⚠：此项目已废弃</strong></p>
                <p>遇到部分加载失败时，尝试刷新</p>
                <p>如非特殊情况，此项目已不再维护</p>
            </div>
        </transition>
    </teleport>
</template>

<script>
export default {
    data() {
        return { isOpen: false };
    },
};
</script>

<style scoped>
@import url("../../assets/transition.css");

div {
    min-width: 50vw;
    max-width: 80vw;
}

@media screen and (max-width: 32rem) {
    div {
        min-width: 75vw;
    }
}

.popup {
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    border: 1px solid rgba(0, 0, 0, 0.1);
    border-radius: 8px;
    padding: 1rem;
    width: 50vw;
    min-height: 50vh;
    background: #fff;
}

.popup a {
    color: cadetblue;
    transition: all 0.3s;
}

.popup a:hover {
    text-decoration: underline;
}

.close {
    cursor: pointer;
}

.flex {
    display: flex;
    align-items: center;
    justify-content: space-between;
}
</style>
