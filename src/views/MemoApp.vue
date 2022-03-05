<template>
  <h1>Vue メモ</h1>
  <!-- <div>
    <select name="" id="" v-model="finish">
      <option value="0">全表示</option>
      <option value="1">未実行</option>
      <option value="2">実行済み</option>
    </select>
  </div> -->
  <div class="memo-list">
    <ul class="memo-list__container">
      <li
        class="memo"
        v-for="(obj, index) in memolist"
        v-bind:key="obj"
        v-bind:style="{ backgroundColor: colors[obj.color] }"
      >
        <div class="memo_checkbox">
          <input
            type="checkbox"
            v-model="memolist[index].flag"
            v-on:change="changeFlag"
          />
          <button class="memo_changecolor" v-on:click="changeColor(index)">
            ☆
          </button>
        </div>
        <div class="memo_text">{{ obj.memo }}</div>
        <button class="memo_delete" v-on:click="deleteButton(obj)">削除</button>
      </li>
    </ul>
    <div class="add-memo-field">
      <input
        class="add-memo-field__input"
        type="text"
        v-on:keydown.enter="saveMemo"
        v-model="inputmemo"
      />
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
      // flaglist: [],
      flag: true,
      finish: 0,
      colors: ["white", "#ff9d9d", "#b7f7a3", "#f7f1a3"],
    }
  },
  methods: {
    saveMemo: function () {
      if (this.inputmemo) {
        this.memolist.push({ flag: false, color: 0, memo: this.inputmemo })
        // this.flaglist.push(false)
        let list_json = JSON.stringify(this.memolist)
        localStorage.setItem("memo", list_json)
        this.inputmemo = ""
      }
    },
    deleteButton: function (obj) {
      const i = this.memolist.indexOf(obj)
      // console.log(str + i)
      // console.log(`${i}, ${str}`)
      this.memolist.splice(i, 1)
      let list_json = JSON.stringify(this.memolist)
      localStorage.setItem("memo", list_json)
    },
    changeFlag: function () {
      // if (this.memolist[index].flag === false) {
      //   this.memolist[index].flag = true
      // } else {
      //   this.memolist[index].flag = false
      // }
      let list_json = JSON.stringify(this.memolist)
      localStorage.setItem("memo", list_json)
    },
    changeColor: function (index) {
      const variation = 4 - 1
      const i = this.memolist[index].color
      var color
      if (i < variation) {
        color = i + 1
      } else {
        color = 0
      }
      this.memolist[index].color = color
      let list_json = JSON.stringify(this.memolist)
      localStorage.setItem("memo", list_json)
    },
    clickEnter: function () {
      this.saveMemo()
    },
  },
  computed: {
    outputList: function () {
      let output = []
      if (this.finish === "0") {
        output = this.memolist
      } else if (this.finish === "1") {
        for (let i = 0; i < this.memolist.length; i++) {
          if (this.memolist[i].flag === false) {
            output.push(this.memolist[i])
          }
        }
      } else {
        for (let i = 0; i < this.memolist.length; i++) {
          if (this.memolist[i].flag === true) {
            output.push(this.memolist[i])
          }
        }
      }
      return output
    },
  },
  created: function () {
    const m = JSON.parse(localStorage.getItem("memo"))
    // console.log(m)
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
  /* color: white; */
  /* background-color: #b23b61; */
  border: 3px solid black;
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

.memo_changecolor {
  background-color: transparent;
  border-radius: 5px;
}
</style>
