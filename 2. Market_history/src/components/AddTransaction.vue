<template>
  <h3>Добавить транзакцию</h3>
  <from id="form">
    <div class="form-control">
      <label for="text">Текст</label>
      <input type="text" id="text" placeholder="Введите текст..." />
    </div>

    <div class="form-control">
      <label for="amount"
        >Сумма <br />
        (отрицательное - расход, положительное - доход)
      </label>
      <input type="number" id="amount" placeholder="Введите сумму" />
    </div>
    <button class="btn">Добавить транщакцию</button>
  </from>
</template>
