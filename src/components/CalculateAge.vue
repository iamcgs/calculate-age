<template>
  <div class="calculate-age">
    <h2>Calcular edad</h2>
    <div class="calculator">
      <div class="input-container">
        <div class="input-date">
          <label>Fecha Inicial (nacimiento): </label><br />
          <input
            class="input"
            type="date"
            v-model="firstDate"
            :max="new Date().toISOString().split('T')[0]"
          />
        </div>
        <div class="input-date">
          <label>Segunda Fecha: </label><br />
          <input
            class="input"
            type="date"
            v-model="secondDate"
            :max="new Date().toISOString().split('T')[0]"
          />
        </div>
      </div>
      <div class="result-container">
        <h3 v-if="firstDate && secondDate && ageGap > 0">
          Edad al día {{ secondDate }}: <br />
          <span>{{ ageGap }} años</span>
        </h3>
        <div v-else-if="firstDate && secondDate && ageGap < 0">
          <p class="error-msg">
            <i>{{ errorMsg }}</i>
          </p>
          <button class="btn-retry" @click="handleRetry">Reintentar</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CalculateAge',
  data() {
    return {
      firstDate: '',
      secondDate: '',
      errorMsg:
        'La segunda fecha no puede ser de un año anterior a la Fecha de Nacimiento. Por favor, revisá las fechas ingresadas y volvé a intentarlo.',
    };
  },

  computed: {
    ageGap() {
      const firstDate = this.firstDate;
      const secondDate = this.secondDate;

      let firstDateYear = firstDate.slice(0, 4);
      let secondDateYear = secondDate.slice(0, 4);

      let firstDateMonth = firstDate.slice(5, 7);
      let secondDateMonth = secondDate.slice(5, 7);

      let firstDateDay = firstDate.slice(8, 10);
      let secondDateDay = secondDate.slice(8, 10);

      let ageDifference = secondDateYear - firstDateYear;
      let monthDifference = secondDateMonth - firstDateMonth;

      if (
        monthDifference < 0 ||
        (monthDifference === 0 && secondDateDay < firstDateDay)
      ) {
        ageDifference = ageDifference - 1;
        console.log(ageDifference);
      }
      return ageDifference;
    },

    handleRetry() {
      this.firstDate = '';
      this.secondDate = '';
    },
  },
};
</script>
<style>
body {
  box-sizing: border-box;
}

.calculate-age {
  color: rgb(102, 101, 101);
  width: 650px;
  margin: 0 auto;
  background: #fcfcfc;
  border-radius: 5px;
  padding: 20px;
  box-shadow: 0px 0px 4px 1px rgba(217, 219, 218, 0.72);
  margin-bottom: 25px;
}

.calculator {
  padding: 20px;
}

.input-container {
  display: flex;
  justify-content: space-around;
  align-items: center;
}

.input-date {
  width: 100%;
  height: 80px;
  margin: 5px;
  background: #f1f9f5;
  padding: 20px;
  border-radius: 5px;
}

.calculate-age h2 {
  font-style: italic;
}

.input-date label {
  color: #40916c;
  font-weight: bold;
  font-style: italic;
}

.input-date input {
  width: 80%;
  border: none;
  text-align: center;
  text-transform: uppercase;
  min-height: 30px;
  margin: 10px auto;
  background: #ffffff;
}

.input-date input:focus {
  outline: none;
  box-shadow: 0px 0px 6px 1px rgba(217, 219, 218, 0.72);
  color: #40916c;
}

.input-date label {
  width: 80%;
}

.result-container h3 {
  font-style: italic;
  background: #f1f9f5;
  padding: 20px;
  margin: 5px;
  border-radius: 5px;
}

.result-container h3 span {
  color: #40916c;
  font-size: 2rem;
}

.error-msg {
  font-weight: 700;
  font-size: 0.75em;
  line-height: 1.6;
  width: 85%;
  color: #e63946;
  margin: 15px auto;
}

.btn-retry {
  color: #f4f4f4;
  background: #40916c;
  letter-spacing: 0.1rem;
  font-size: 1rem;
  font-weight: bold;
  text-transform: uppercase;
  border: none;
  border-radius: 5px;
  padding: 10px 15px;
  box-shadow: 0px 0px 6px 1px rgba(217, 219, 218, 0.72);
}

.btn-retry:hover {
  opacity: 0.9;
}

@media screen and (max-width: 768px) {
  .calculate-age {
    width: 450px;
  }

  .calculator {
    padding: 20px 40px;
  }

  .input-container {
    flex-direction: column;
  }

  .input-date {
    width: 80%;
    height: 75px;
    margin: 10px;
  }

  .result-container h3 {
    background: none;
  }
}

@media screen and (max-width: 475px) {
  .calculate-age {
    width: 350px;
  }

  .calculator {
    padding: 20px;
  }

  .input-date {
    height: 65px;
  }
}
</style>
