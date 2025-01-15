<template>
  <h3>История</h3>
  <ul id="list" class="list">
    <li
      v-for="t in transactions"
      :key="t.id"
      :class="t.amount < 0 ? 'minus' : 'plus'"
    >
      {{ t.text }}
      <span>{{ t.amount }}руб</span><button class="delete-btn">x</button>
    </li>
    <!-- <li class="minus">
      Деньги <span>-500</span><button class="delete-btn">x</button>
    </li>
    <li class="plus">
      Зарплата <span>+11500</span><button class="delete-btn">x</button>
    </li> -->
  </ul>
</template>

<script>
export default {
  data() {
    return {
      transactions: [
        { id: 1, text: "Цветы", amount: -100 },
        { id: 2, text: "Мяч", amount: -900 },
        { id: 3, text: "Продажа виктории", amount: 450 },
        { id: 4, text: "Тортик", amount: -650 },
      ],
    };
  },
};
</script>
