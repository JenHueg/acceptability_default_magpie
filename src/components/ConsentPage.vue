<template>
  <div class="page">
    <h2>Einverständniserklärung</h2>

    <p>
      Bitte lesen Sie die folgenden Punkte aufmerksam durch
      und bestätigen Sie jeden einzelnen Punkt.
    </p>

    <div class="consent-list">
      <label
        v-for="(point, index) in consentPoints"
        :key="index"
        class="consent-item"
      >
        <input
          type="checkbox"
          v-model="accepted[index]"
        />
        <span>{{ point }}</span>
      </label>
    </div>

    <p v-if="showWarning" class="warning">
      Ohne Ihr Einverständnis können Sie leider nicht an
      der Studie teilnehmen.
    </p>

    <button
      type="button"
      class="next-button"
      :class="{ ready: allAccepted }"
      @click="continueNext"
    >
      Weiter
    </button>
  </div>
</template>

<script>
export default {
  name: 'ConsentPage',

  data() {
    return {
      consentPoints: [
        'ENTER POINT',
        'ENTER POINT',
        'ENTER POINT',
        'ENTER POINT',
        'ENTER POINT',
        'ENTER POINT',
      ],

      accepted: [false, false, false, false, false, false],
      showWarning: false
    }
  },

  computed: {
    allAccepted() {
      return this.accepted.every(value => value === true)
    }
  },

  methods: {
    continueNext() {
      if (!this.allAccepted) {
        this.showWarning = true
        return
      }

      this.showWarning = false
      this.$emit('next')
    }
  }
}
</script>

<style scoped>
.page {
  max-width: 700px;
  margin: 40px auto;
  padding: 0 20px;
  font-family: Arial, sans-serif;
  text-align: left;
}

.consent-list {
  margin: 24px 0;
}

.consent-item {
  display: flex;
  align-items: flex-start;
  gap: 12px;
  margin-bottom: 18px;
  line-height: 1.5;
  cursor: pointer;
}

.consent-item input {
  margin-top: 5px;
  flex-shrink: 0;
}

.next-button {
  background-color: #bdbdbd;
  color: white;
  border: none;
  border-radius: 6px;
  padding: 12px 28px;
  font-size: 16px;
  cursor: pointer;
}

.next-button.ready {
  background-color: #1976d2;
}

.warning {
  color: #b00020;
  margin-top: 20px;
  font-weight: bold;
}
</style>