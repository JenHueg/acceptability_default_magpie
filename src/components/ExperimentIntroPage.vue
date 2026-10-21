
<template>
  <div class="page">
    <h2>Das eigentliche Experiment beginnt</h2>

    <p>
      Vielen Dank! Sie haben den Übungsteil abgeschlossen.
    </p>

    <p>
      Jetzt beginnt das eigentliche Experiment.
      Bitte lesen Sie weiterhin aufmerksam und beantworten
      Sie die Fragen so, wie es Ihrem persönlichen Urteil entspricht.
    </p>

    <button @click="$emit('next')">
      Experiment starten
    </button>
  </div>
</template>

<script>
export default {
  name: 'ExperimentIntroPage'
}
</script>

<style scoped>
.page {
  max-width: 700px;
  margin: 40px auto;
  padding: 0 20px;
  text-align: center;
  font-family: Arial, sans-serif;
}

button {
  background-color: #1976d2;
  color: white;
  border: none;
  border-radius: 6px;
  padding: 12px 28px;
  font-size: 16px;
  cursor: pointer;
}
</style>
