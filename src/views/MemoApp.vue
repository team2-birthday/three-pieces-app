<template>
  <h1>Vue メモ</h1>
  <div>
    <select name="" id="" v-model="finish">
      <option value="0">全表示</option>
      <option value="1">未実行</option>
      <option value="2">実行済み</option>
    </select>
  </div>
  <div class="memo-list">
    <ul class="memo-list__container">
      <li class="memo" v-for="memo in memolist" v-bind:key="memo">
        <div class="memo_checkbox">
          <input type="checkbox" class="checkbox" />
        </div>
        <div class="memo_text">{{ memo }}</div>
        <button class="memo_delete" v-on:click="deleteButton(memo)">
          削除
        </button>
      </li>
    </ul>
    <div class="add-memo-field">
      <input class="add-memo-field__input" type="text" v-model="inputmemo" />
      <button class="add-memo-field__button" v-on:click="saveMemo">追加</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      inputmemo: "",
      memolist: [],
    }
  },
  methods: {
    saveMemo: async function () {
      if (this.inputmemo) {
        this.memolist.push(this.inputmemo)
        let list_json = JSON.stringify(this.memolist)
        await localStorage.setItem("memo", list_json)
        this.inputmemo = ""
      }
    },
    deleteButton: async function (str) {
      const i = this.memolist.indexOf(str)
      // console.log(str + i)
      // console.log(`${i}, ${str}`)
      this.memolist.splice(i, 1)
      let list_json = JSON.stringify(this.memolist)
      await localStorage.setItem("memo", list_json)
    },
  },
  computed: {
    outputList: function () {
      const listJson = localStorage.getItem("memo")
      const listofmemo = JSON.parse(listJson)
      return listofmemo
    },
  },
  created: function () {
    const m = JSON.parse(localStorage.getItem("memo"))
    console.log(m)
    if (m) {
      // console.log(m)
      this.memolist = [...m]
    } else {
      localStorage.setItem("memo", "[]")
    }
  },
}
</script>

<style scoped>
.memo-list {
  padding-left: 5rem;
  padding-right: 5rem;
  display: flex;
  flex-direction: column;
  align-items: stretch;
  max-width: 512px;
  margin-left: auto;
  margin-right: auto;
}

.memo-list__container {
  padding: 0;
}

.memo {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0.5rem;
  border-radius: 5px;
}

.memo:hover {
  color: white;
  background-color: #b23b61;
}

.memo__text {
  margin-left: 2rem;
  text-align: left;
}

.memo__text--done {
  text-decoration-line: line-through;
}

.memo__delete {
  margin-left: 1rem;
  padding: 0.5rem 0.5rem;
  border: solid 1px black;
  border-radius: 5px;
  background-color: white;
}

.memo__delete:hover {
  background-color: #b2ae3b;
  border-radius: 5px;
}

.add-memo-field {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.add-memo-field__input {
  padding: 10px;
}
.add-memo-field__button {
  padding: 0.5rem 0.5rem;
  border: solid 1px black;
  border-radius: 5px;
  background-color: white;
}

.add-memo-field__button:hover {
  background-color: #b2ae3b;
  border-radius: 5px;
}
</style>
