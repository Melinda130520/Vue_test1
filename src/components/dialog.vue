<template>
    <div>
        <div class="dialog-wrap">
            <!-- 蒙版 -->
            <div class="dialog-cover" @click="closeMyself" v-if="isShow"></div>
            <!-- dialog内容 -->
            <transition name="drop">
                <div class="dialog-content" v-if="isShow" >
                    <p class="dialog-close" @click="closeMyself">x</p>
                    <!-- 插槽 -->
                    <slot>empty</slot>
                </div>
            </transition>
        </div>
    </div>
</template>

<script>
export default {
    props : {
        isShow : {               //dialog是否显示
            type : Boolean,
            default : false
        }
    },
    data () {
        return {
      
        }
    },
    methods: {
        closeMyself (){    //关闭dialog对话框，并且将事件传给父组件
            this.$emit('on-close');
        }
    }   
}
</script>

<style scoped>
    .drop-enter-active {
        transition: all .5s ease;
    }
    .drop-leave-active {
        transition: all .3s ease;
    }
    .drop-enter {
        transform: translateY(-500px);
    }
    .drop-leave-active {
        transform: translateY(-500px);
    }
    .dialog-wrap {
        position: fixed;
        width: 100%;
        height: 100%;
        /*top:0;*/    
    }
    .dialog-cover {
        background: #000;
        opacity: .3;
        position: fixed;
        z-index: 5;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
    }
    .dialog-content {
        width: 50%;
        position: fixed;
        max-height: 50%;
        overflow: auto;
        background: #fff;
        top: 20%;
        left: 50%;
        margin-left: -25%;
        z-index: 10;
        border: 2px solid #464068;
        padding: 2%;
        line-height: 1.6;
    }
    .dialog-close {
        position: absolute;
        right: 5px;
        top: 5px;
        width: 20px;
        height: 20px;
        text-align: center;
        cursor: pointer;
    }
    .dialog-close:hover {
        color: #4fc08d;
    }
</style>
