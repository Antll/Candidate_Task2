<template>
  <div id="app">
    <form @submit.prevent="alertPossibleTurns">
      <label for="initialPlacing">Исходное положение:</label>
      <input type="text" name="initialPlacing" v-model="initialPlacing">
      <input class="btn" type="submit" value="Ок">
    </form>
  </div>
</template>

<script>

export default {
  name: 'App',

  data() {
    return {
      initialPlacing: '',
    };
  },

  methods: {
    alertPossibleTurns() {
      const yCoord = 'ABCDEFGH';
      const xCoord = '87654321';

      /**
       * Корректные координаты:
       * 1-ый символ должен быть буквой от A до H
       * 2-ой символ должен быть цифрой от 1 до 9
       */
      if (
        !yCoord.includes(this.initialPlacing.charAt(0))
        || !xCoord.includes(this.initialPlacing.charAt(1))
        || this.initialPlacing.length !== 2
      ) {
        alert('Неккоректно введённые данные');
      } else {
        /**
         * Для каждой возможной позиции проверяем
         * не выходит ли она за границы поля.
         * Если не выходит, то добавляем в ответ.
         */
        let possiblePlacingString = '';

        //  y - 1; x + 2
        let possibleCoord =
          String.fromCharCode(this.initialPlacing.charCodeAt(0) - 1) +
          String.fromCharCode(this.initialPlacing.charCodeAt(1) + 2);
        if (
          yCoord.includes(possibleCoord.charAt(0))
          && xCoord.includes(possibleCoord.charAt(1))
        ) {
          possiblePlacingString += `${possibleCoord}`;
        }

        // y + 1; x + 2
        possibleCoord =
          String.fromCharCode(this.initialPlacing.charCodeAt(0) + 1) +
          String.fromCharCode(this.initialPlacing.charCodeAt(1) + 2);
        if (
          yCoord.includes(possibleCoord.charAt(0))
          && xCoord.includes(possibleCoord.charAt(1))
        ) {
          possiblePlacingString += ` ${possibleCoord}`;
        }

        // y + 2; x + 1
        possibleCoord =
          String.fromCharCode(this.initialPlacing.charCodeAt(0) + 2) +
          String.fromCharCode(this.initialPlacing.charCodeAt(1) + 1);
        if (
          yCoord.includes(possibleCoord.charAt(0))
          && xCoord.includes(possibleCoord.charAt(1))
        ) {
          possiblePlacingString += ` ${possibleCoord}`;
        }

        // y + 2; x - 1
        possibleCoord =
          String.fromCharCode(this.initialPlacing.charCodeAt(0) + 2) +
          String.fromCharCode(this.initialPlacing.charCodeAt(1) - 1);
        if (
          yCoord.includes(possibleCoord.charAt(0))
          && xCoord.includes(possibleCoord.charAt(1))
        ) {
          possiblePlacingString += ` ${possibleCoord}`;
        }

        // y + 1; x - 2
        possibleCoord =
          String.fromCharCode(this.initialPlacing.charCodeAt(0) + 1) +
          String.fromCharCode(this.initialPlacing.charCodeAt(1) - 2);
        if (
          yCoord.includes(possibleCoord.charAt(0))
          && xCoord.includes(possibleCoord.charAt(1))
        ) {
          possiblePlacingString += ` ${possibleCoord}`;
        }

        // y - 1; x - 2
        possibleCoord =
          String.fromCharCode(this.initialPlacing.charCodeAt(0) - 1) +
          String.fromCharCode(this.initialPlacing.charCodeAt(1) - 2);
        if (
          yCoord.includes(possibleCoord.charAt(0))
          && xCoord.includes(possibleCoord.charAt(1))
        ) {
          possiblePlacingString += ` ${possibleCoord}`;
        }

        // y - 2; x - 1
        possibleCoord =
          String.fromCharCode(this.initialPlacing.charCodeAt(0) - 2) +
          String.fromCharCode(this.initialPlacing.charCodeAt(1) - 1);
        if (
          yCoord.includes(possibleCoord.charAt(0))
          && xCoord.includes(possibleCoord.charAt(1))
        ) {
          possiblePlacingString += ` ${possibleCoord}`;
        }

        // y - 2; x + 1
        possibleCoord =
          String.fromCharCode(this.initialPlacing.charCodeAt(0) - 2) +
          String.fromCharCode(this.initialPlacing.charCodeAt(1) + 1);
        if (
          yCoord.includes(possibleCoord.charAt(0))
          && xCoord.includes(possibleCoord.charAt(1))
        ) {
          possiblePlacingString += ` ${possibleCoord}`;
        }

        // Выводим получившийся ответ
        alert(`Возможные варианты хода:\n ${possiblePlacingString}`);
      }
    },
  },
};
</script>

<style>
form {
  block: inline-block;
  width: 200px;
  margin-top: 10px;
}

.btn {
  margin-top: 10px;
  width: 80px;
}

</style>
