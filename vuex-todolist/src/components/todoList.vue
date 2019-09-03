<template>
  <div class="todolist">
    <h2>Vuex todo list</h2>
    <p>Simple Todo List with adding and filter by diff status.</p>

    <input type="text" class="input-text" name="listItem" placeholder="input your plan..." />
    <div class="input-btn">Add</div>
    <br />

    <ol>
      <li v-for="(item, index) in todoList" :key="index">
        <span>{{ index + 1 }}.</span>
        <input type="checkbox" name="done-todo" class="done-todo" @click="finishHandle(item)"/>
        <span :class="{finished: item.isFinished}">{{ item.content }}</span>
      </li>
    </ol>

    <ul>
      <li v-for="btnItem in btnGroup" :key="btnItem">
        <a href="#" data-filter="btnItem.itemFilter" class="selected">{{ btnItem.name }}</a>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "TodoList",
  props: {},
  data() {
    return {
      todoList: [
          {
            content: "sing",
            isFinished: false
          },
          {
              content: "play",
              isFinished: false
          },
          {
              content: "eat",
              isFinished: false
          }
      ],
      btnGroup: [
        {
          itemFilter: "all",
          name: "All"
        },
        {
          itemFilter: "active",
          name: "Active"
        },
        {
          itemFilter: "complete",
          name: "Complete"
        }
      ]
    };
  },
  methods: {
      finishHandle: function (item) {
          item.isFinished = !item.isFinished;
      }
  }
};
</script>

<style scoped>
.todolist {
  width: 600px;
  height: auto;
  margin: 50px auto;
  border-radius: 6px;
  background-color: antiquewhite;
}
h2 {
  font-size: 1.8em;
  font-weight: bolder;
  padding-top: 20px;
}
p {
  font-style: italic;
}
.input-text {
  width: 60%;
  padding: 6px 16px;
  margin-right: 10px;
}
.input-btn {
  display: inline-block;
  width: 30px;
  background-color: #fc999b;
  color: #ffffff;
  padding: 6px 16px;
}
ol{
    text-align: left;
    margin-left: 20px;
}
ol li{
    display: block;
    margin-bottom: 6px;
}
ol li .finished{
    text-decoration: line-through;
}
ul {
  list-style-type: none;
  padding: 0;
}
ul li {
  display: inline-block;
  margin: 16px;
}
ul li a {
  color: #42b983;
  text-decoration: none;
  width: 20px;
  padding: 2px 16px;
}
ul li a.selected{
    border: 1px solid #42b983;
}
</style>
