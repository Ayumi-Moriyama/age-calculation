<script setup>
import { ref , computed } from 'vue'
// const count = ref(0)
const date = new Date()
const year = date.getFullYear()

// getMonthは0からスタートするので今月は+1する
const month = date.getMonth() +1 
const day = date.getDate()

// ユーザーの名前
const userName = ref('')

// ユーザーの生年月日
const selectedMonth = ref('')
const selectedDay = ref('')
const userInputYear = ref('')

// 現在の月と誕生月を比較して絶対値で返す
// 誕生月が現在の月以上の数字のとき 7-7=0 10-7=3 12-7=5 →誕生月から現在の月を引く
// 誕生月が現在の月より小さいときは 6-7=-1 3-7=-4 12-4=8 →12から絶対値を引く

// 次の誕生日までの月数を計算するcomputedプロパティ
const userBirthMonth = computed(() => {
  if (!selectedMonth.value) return ''
  const birthMonth = parseInt(selectedMonth.value)
  if (birthMonth >= month) {
    return birthMonth - month
  } else {
    return 12 - (month - birthMonth)
  }
})

// 年齢を計算するcomputedプロパティ
const userAge = computed(() => {
  if (!userInputYear.value || !selectedMonth.value || !selectedDay.value) return ''
  const birthYear = parseInt(userInputYear.value)
  const birthMonth = parseInt(selectedMonth.value)
  const birthDay = parseInt(selectedDay.value)
  
  let age = year - birthYear
  
  // 現在の月日が誕生日を過ぎていない場合、年齢を1歳減らす
  if (month < birthMonth || (month === birthMonth && day < birthDay)) {
    age -= 1
  }
  
  return age
})

</script>

<template>
  <div class="background">
    <h1>年齢計算</h1>

    <div class="card-container">
        <div class="card1">
          <div class="box1">
            <div>
              <p class="content1">今日は {{ year }} 年 {{ month }} 月 {{ day }} 日</p>
            </div>
          </div>
        </div>
    </div>
      <h2>名前を入力してください</h2>
        <div class="container">
          <input v-model="userName" type="text" placeholder="ニックネーム可">
        </div>
        

      <h2>生年月日を入力してください</h2>
      <div class="container">
        <table>
          <tr>
            <th>生まれた年（西暦）</th><th>誕生月</th><th>誕生日</th>
          </tr>
          <tr>
            <td>
              <input v-model.number="userInputYear" placeholder="半角数字で入力" />
            </td>
            <td>
            <select v-model.number="selectedMonth">
              <option disabled value="">月</option>
              <option>1</option>
              <option>2</option>
              <option>3</option>
              <option>4</option>
              <option>5</option>
              <option>6</option>
              <option>7</option>
              <option>8</option>
              <option>9</option>
              <option>10</option>
              <option>11</option>
              <option>12</option>
            </select>
            </td>
            <td>
            <select v-model.number="selectedDay">
              <option disabled value="">日</option>
              <option>1</option>
              <option>2</option>
              <option>3</option>
              <option>4</option>
              <option>5</option>
              <option>6</option>
              <option>7</option>
              <option>8</option>
              <option>9</option>
              <option>10</option>
              <option>11</option>
              <option>12</option>
              <option>13</option>
              <option>14</option>
              <option>15</option>
              <option>16</option>
              <option>17</option>
              <option>18</option>
              <option>19</option>
              <option>20</option>
              <option>21</option>
              <option>22</option>
              <option>23</option>
              <option>24</option>
              <option>25</option>
              <option>26</option>
              <option>27</option>
              <option>28</option>
              <option>29</option>
              <option>30</option>
              <option>31</option>
            </select>
            </td>
          </tr>
        </table>
      </div>

      <div class="container">
        <div class="card-container">
          <div class="card2">
            <div class="box1">
              <div>
                <p class="title1">私の名前は {{ userName }}</p>
                <p class="title1">生年月日は
                  {{ userInputYear }} 年
                  {{ selectedMonth }} 月
                  {{ selectedDay }} 日
                です
                </p>
              </div>
            </div>
          </div>
        </div>
        <div class="box2">
          <p>現在の年齢：{{ userAge }} 歳</p>
          <p>次の誕生日まであと{{ userBirthMonth }} ヶ月</p>
        </div>
      </div>
  </div>
</template>
