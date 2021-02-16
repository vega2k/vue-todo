<template>
    <div class="inputBox shadow">
        <input type="text" ref="newTodoItem" v-model="newTodoItem" v-on:keyup.enter="addTodo">
        <span class="addContainer" v-on:click="addTodo">
            <i class="fas fa-plus addBtn"></i>
        </span>
        <!-- <button @click="addTodo">add</button> -->
    </div>
</template>

<script>
export default {
    data:function() {
        return {
            newTodoItem: ""
        }
    },
    mounted() {
      this.$refs.newTodoItem.focus();
    },
    methods:{
        addTodo:function() {
            if (this.newTodoItem !== '') {
                var obj = {completed: false, item:this.newTodoItem};
                console.log(obj);
                //JSON.stringify는 object를 json string 으로 변환
                localStorage.setItem(this.newTodoItem,JSON.stringify(obj));
                this.clearInput();
            //     var value = this.newTodoItem && this.newTodoItem.trim();
            //     localStorage.setItem(value,value);
            //     this.clearInput();
            }
        },
        clearInput:function() {
            //addTodo() 함수에 있었지만 clearInput()함수로 이동            
            this.newTodoItem = '';
        }
    }
}
</script>

<style scoped>
input:focus {
  outline: none;
}
.inputBox {
  background: white;
  height: 50px;
  line-height: 50px;
  border-radius: 15px;
}
.inputBox input {
  border-style: none;
  font-size: 0.9rem;
}
.addContainer {
  float: right;
  background: linear-gradient(to right, #6478FB, #8763FB);
  display: block;
  width: 3rem;
  border-radius: 0 5px 5px 0;
}
.addBtn {
  color: white;
  vertical-align: middle;
}
</style>
