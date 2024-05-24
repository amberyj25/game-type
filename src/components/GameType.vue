
<template>
  <div>
    <div class="game">
      <table>
        <thead>
          <tr>
            <th>Game ID</th>
            <th>Game Name</th>
            <th>Rank Data</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="game in data" :key="game.GameID">
            <td>{{ game.GameID }}</td>
            <td>{{ game.GameName }}</td>
            <td>{{ numberWithCommas(game.RankData) }}</td>
          </tr>
        </tbody>
      </table>
    </div>
    <div class="timer">{{ formatTime(countdown) }}</div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const data = ref([{
  GameID: 1,
  GameName: "A",
  RankData: 1777777
},{
  GameID: 2,
  GameName: "B",
  RankData: 2000
},{
  GameID: 3,
  GameName: "C",
  RankData: 300000
},{
  GameID: 4,
  GameName: "D",
  RankData: 5000000
},{
  GameID: 5,
  GameName: "E",
  RankData: 4000000
},{
  GameID: 6,
  GameName: "F",
  RankData: 4000000
},{
  GameID: 7,
  GameName: "G",
  RankData: 4000000
}]);

const initialTime = 4000000;
const countdown = ref(initialTime);

onMounted(() => {
  timer;
});

const numberWithCommas = (number) => {
  let numberString = number.toString();
  return numberString.replace(/\B(?=(\d{3})+(?!\d))/g, ",");
};

const timer = setInterval(() => {
  countdown.value -= 1000;
}, 1000);

    // 格式化时间的辅助函数
const formatTime = (time) => {

  const seconds = Math.floor((time / 1000) % 60);
  const minutes = Math.floor((time / (1000 * 60)) % 60);
  const hours = Math.floor((time / (1000 * 60 * 60)) % 24);
  return `${hours.toString().padStart(2, '0')}:${minutes.toString().padStart(2, '0')}:${seconds.toString().padStart(2, '0')}`;
};
</script>

<style scoped>
.game {
  width: 750px;
  height: 400px;
  border: 5px solid red;
  border-radius: 25px;
  background-color: #FFA042;
}

table {
  width: 100%;
  border-collapse: collapse;
}

th, td {
  text-align: center;
  padding: 10px;
}

th {
  font-size: 25px;
}

td {
  font-size: 20px;
}

.timer {
  display: flex;
  justify-content: center;
  font-size: 45px;
  margin: 25px 0;
  color: #0000E3;
}
</style>