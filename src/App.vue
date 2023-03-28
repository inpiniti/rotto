<template>
  <select name="fruit">
    <option value="바나나">바나나</option>
    <option value="사과">사과</option>
    <option value="파인애플">파인애플</option>
  </select>
  <div class="divTableBody">
    <div class="divTableRow">
      <div class="divTableCell color0" :style="{ opacity: 로또[0] }">1</div>
      <div class="divTableCell color0" :style="{ opacity: 로또[1] }">2</div>
      <div class="divTableCell color0" :style="{ opacity: 로또[2] }">3</div>
      <div class="divTableCell color0" :style="{ opacity: 로또[3] }">4</div>
      <div class="divTableCell color0" :style="{ opacity: 로또[4] }">5</div>
      <div class="divTableCell color0" :style="{ opacity: 로또[5] }">6</div>
      <div class="divTableCell color0" :style="{ opacity: 로또[6] }">7</div>
      <div class="divTableCell color0" :style="{ opacity: 로또[7] }">8</div>
      <div class="divTableCell color0" :style="{ opacity: 로또[8] }">9</div>
      <div class="divTableCell color0" :style="{ opacity: 로또[9] }">10</div>
    </div>
    <div class="divTableRow">
      <div class="divTableCell color1" :style="{ opacity: 로또[10] }">11</div>
      <div class="divTableCell color1" :style="{ opacity: 로또[11] }">12</div>
      <div class="divTableCell color1" :style="{ opacity: 로또[12] }">13</div>
      <div class="divTableCell color1" :style="{ opacity: 로또[13] }">14</div>
      <div class="divTableCell color1" :style="{ opacity: 로또[14] }">15</div>
      <div class="divTableCell color1" :style="{ opacity: 로또[15] }">16</div>
      <div class="divTableCell color1" :style="{ opacity: 로또[16] }">17</div>
      <div class="divTableCell color1" :style="{ opacity: 로또[17] }">18</div>
      <div class="divTableCell color1" :style="{ opacity: 로또[18] }">19</div>
      <div class="divTableCell color1" :style="{ opacity: 로또[19] }">20</div>
    </div>
    <div class="divTableRow">
      <div class="divTableCell color2" :style="{ opacity: 로또[20] }">21</div>
      <div class="divTableCell color2" :style="{ opacity: 로또[21] }">22</div>
      <div class="divTableCell color2" :style="{ opacity: 로또[22] }">23</div>
      <div class="divTableCell color2" :style="{ opacity: 로또[23] }">24</div>
      <div class="divTableCell color2" :style="{ opacity: 로또[24] }">25</div>
      <div class="divTableCell color2" :style="{ opacity: 로또[25] }">26</div>
      <div class="divTableCell color2" :style="{ opacity: 로또[26] }">27</div>
      <div class="divTableCell color2" :style="{ opacity: 로또[27] }">28</div>
      <div class="divTableCell color2" :style="{ opacity: 로또[28] }">29</div>
      <div class="divTableCell color2" :style="{ opacity: 로또[29] }">30</div>
    </div>
    <div class="divTableRow">
      <div class="divTableCell color3" :style="{ opacity: 로또[30] }">31</div>
      <div class="divTableCell color3" :style="{ opacity: 로또[31] }">32</div>
      <div class="divTableCell color3" :style="{ opacity: 로또[32] }">33</div>
      <div class="divTableCell color3" :style="{ opacity: 로또[33] }">34</div>
      <div class="divTableCell color3" :style="{ opacity: 로또[34] }">35</div>
      <div class="divTableCell color3" :style="{ opacity: 로또[35] }">36</div>
      <div class="divTableCell color3" :style="{ opacity: 로또[36] }">37</div>
      <div class="divTableCell color3" :style="{ opacity: 로또[37] }">38</div>
      <div class="divTableCell color3" :style="{ opacity: 로또[38] }">39</div>
      <div class="divTableCell color3" :style="{ opacity: 로또[39] }">40</div>
    </div>
    <div class="divTableRow">
      <div class="divTableCell color4" :style="{ opacity: 로또[40] }">41</div>
      <div class="divTableCell color4" :style="{ opacity: 로또[41] }">42</div>
      <div class="divTableCell color4" :style="{ opacity: 로또[42] }">43</div>
      <div class="divTableCell color4" :style="{ opacity: 로또[43] }">44</div>
      <div class="divTableCell color4" :style="{ opacity: 로또[44] }">45</div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";

const 당첨번호목록 = ref({
  //1060: [3, 10, 24, 33, 38, 45, 36],
  //1059: [7, 10, 22, 25, 34, 40, 27],
  //1058: [11, 23, 25, 30, 32, 40, 42],
  //1057: [11, 23, 25, 30, 32, 40, 42],
  //1056: [8, 13, 19, 27, 40, 45, 12],
});

const 로또 = ref([
  1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1,
  1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1,
]);

const 로또색상변경 = () => {
  Object.values(당첨번호목록.value)
    .reverse()
    .forEach((회차, index): any => {
      회차.map((당첨번호) => {
        로또.value[당첨번호 - 1] =
          로또.value[당첨번호 - 1] - 0.6 ** (index + 1);
      });
    });
};

const click = async () => {
  console.log("click");
  const data = await fetch(
    "https://cors-anywhere.herokuapp.com/http://www.dhlottery.co.kr/common.do?method=getLottoNumber&drwNo=100",
    {
      method: "GET", // *GET, POST, PUT, DELETE, etc.
      mode: "cors", // no-cors, *cors, same-origin
      cache: "no-cache", // *default, no-cache, reload, force-cache, only-if-cached
      headers: {
        "Content-Type": "application/json",
        origin: "x-requested-with",
        // 'Content-Type': 'application/x-www-form-urlencoded',
      },
      referrerPolicy: "no-referrer", // no-referrer, *no-referrer-when-downgrade, origin, origin-when-cross-origin, same-origin, strict-origin, strict-origin-when-cross-origin, unsafe-url
    }
  ).then((response) => {
    if (response.ok) {
      return response.json(); //then consume it again, the error happens
    }
  });

  console.log("data", data);
  당첨번호목록.value[data.drwNo] = [
    data.drwtNo1,
    data.drwtNo2,
    data.drwtNo3,
    data.drwtNo4,
    data.drwtNo5,
    data.drwtNo6,
    data.bnusNo,
  ];
  console.log("당첨번호목록", 당첨번호목록.value);

  로또색상변경();
};

click();

//console.log("로또", 로또.value);
</script>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}

.divTable {
  display: table;
  width: 100%;
}
.divTableRow {
  display: flex;
}
.divTableCell,
.divTableHead {
  border-radius: 25px;
  display: inline-block;
  width: 25px;
  height: 25px;
  padding: 7px;
  margin: 10px;
  color: #000;
}
.opacity {
  opacity: 0.8;
}
.color0 {
  background-color: #fbc400;
}

.color1 {
  background-color: #69c8f2;
}

.color2 {
  background-color: #ff7272;
}

.color3 {
  background-color: #767676;
}

.color4 {
  background-color: #b0d840;
}
</style>
