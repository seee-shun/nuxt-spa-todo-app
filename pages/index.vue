<template>
  <section class="container">
    <h1 class="title">To do List</h1>
    <div class="addArea">
      <form @submit.prevent="addList">
        <input
          class="input"
          v-model="newList"
          type="text"
          placeholder="TO DOリストを追加してください"
        />
        <input type="submit" value="Add" class="button" />
      </form>
    </div>
    <div class="filterArea">
      <button class="button">TO DO</button>
      <button class="button">PENDING</button>
      <button class="button">IN PROGRESS</button>
      <button class="button">Done</button>
    </div>
    <table class="lists">
      <thead>
        <tr>
          <th>Task</th>
          <th>CreateDate</th>
          <th>Status</th>
          <th>del</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(item, index) in todos" v-bind:key="index">
          <td>{{ item.content }}</td>
          <td>{{ item.createDate }}</td>
          <td>
            <button class="button">{{ item.status }}</button>
          </td>
          <td>
            <button class="button" @click="deleteList(item[index])">
              DELETE
            </button>
          </td>
        </tr>
      </tbody>
    </table>
  </section>
</template>

<script>
export default {
  data() {
    return {
      todos: [
        // { content: 'テスト', createDate: '2020-04-30 17:00', status: '作業前' },
        // {
        //   content: 'コーディング',
        //   createDate: '2020-04-30 16:00',
        //   status: '作業中',
        // },
        // { content: '環境構築', createDate: '2020-04-30 15:30', status: '完了' },
      ],
      newList: '',
      newLists: [],
    }
  },
  methods: {
    addList() {
      if (this.newList !== '') {
        this.todos.push({
          content: this.newList,
          createDate: '2020',
          status: 'TO DO',
        })
        this.newList = ''
      }
    },
  },
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  /* display: flex;
  flex-direction: column; */

  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.addArea {
  margin: 40px auto;
}
css table {
  border-collapse: collapse;
  border-spacing: 0;
  width: 100%;
}

table tr {
  border-bottom: solid 1px #eee;
  cursor: pointer;
}

tbody tr:hover {
  background-color: #fcede3;
}

table th,
table td {
  text-align: center;
  width: 25%;
  padding: 15px 10px;
}
.filterArea {
  margin: 20px auto;
}
.input {
  width: 300px;
  height: 40px;
}
.button {
  width: 120px;
  height: 40px;
  padding: 3px;
  text-decoration: none;
  border-radius: 4px;
  font-weight: 700;
  cursor: pointer;
  /* color: #ffffff; */
  /* background-image: linear-gradient(45deg, #ffc107 0%, #ff8b5f 100%); */
  box-shadow: 0px 2px 2px rgba(0, 0, 0, 0.29);
  /* border-bottom: solid 3px #c58668; */
}
button:hover {
  background-color: rgb(255, 219, 173);
}
.lists {
  margin: 3px auto;
}
</style>
