<!-- 列表多选 -->
<template>
    <div class="chooser-component">
        <ul class="chooser-list">
            <li
                v-for="(item, index) in selections"
                @click="checkActive(index)"
                :title="item.label"
                :class="{active: toggleSelection(index)}">
                {{ item.label }}
            </li>
        </ul>
    </div>
</template>

<script type="text/javascript">
    import _ from 'lodash'    //工具库

    export default{
        props : {                              //从父组件中获取参数值
            selections : {
                type : Array,
                default : [
                    {
                        label: 'test',
                        value: 0
                    }
                ]
            }
        },
        data (){
            return { 
                nowIndexes : [0]               //选中的项
            }
        },
        methods : {
            //判断是否选中
            checkActive (index){                    
                // 要是当前选中的索引数组中没有，则添加
                // 否则从当前的索引库中删除
                if (this.nowIndexes.indexOf(index) === -1) {    
                    this.nowIndexes.push(index)  
                }else {
                    this.nowIndexes = _.remove(this.nowIndexes, (idx) => {
                        return idx !== index
                    })
                }

                // 获取选中的值
                let nowObjArray = _.map(this.nowIndexes, (idx) => {
                    return this.selections[idx]
                })
                this.$emit('on-change', nowObjArray)
            },

            //单击选项的时候，判断是取消选中还是选中   
            toggleSelection (index){                
                return this.nowIndexes.indexOf(index) !== -1
            }
        }
    }
</script>

<style scoped>
    .chooser-component {
        position: relative;
        display: inline-block;
    }
    .chooser-list li{
        display: inline-block;
        border: 1px solid #e3e3e3;
        height: 25px;
        line-height: 25px;
        padding: 0 8px;
        margin-right: 5px;
        border-radius: 3px;
        text-align: center;
        cursor: pointer;
    }
    .chooser-list li.active {
        border-color: #4fc08d;
        background: #4fc08d;
        color: #fff;
    }
</style>