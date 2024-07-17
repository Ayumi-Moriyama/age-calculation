<script setup>
import { ref } from 'vue'
// const count = ref(0)
const date = new Date()
const year = date.getFullYear()

// getMonthは0からスタートするので今月は+1する
const month = date.getMonth() +1 
const day = date.getDate()

const selectedMonth = ref('')
const selectedDay = ref('')
const userInput = ref('')

</script>

<template>
  <p>今日は {{ year }} 年 {{ month }} 月 {{ day }} 日</p>
  <p>生年月日を入力してください</p>
  <div>
    生年月日:
      {{ userInput }} 年
      {{ selectedMonth }} 月
      {{ selectedDay }} 日
  </div>
  <div>
    <input v-model.number="userInput" placeholder="生まれた年を数字で入力" />

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
  </div>
  
  <p>現在の年齢：</p>
  <p>次の誕生日まであと</p>
  <!-- <button @click="count++">Count is: {{ count }}</button> -->
</template>

