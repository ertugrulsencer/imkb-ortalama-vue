<template>
  <form v-on:submit.prevent="calculate">
    <input
      type="number"
      min="0"
      max="100"
      v-model="formData.exam1"
      placeholder="1. Sınav"
    />
    <input
      type="number"
      min="0"
      max="100"
      v-model="formData.exam2"
      placeholder="2. Sınav"
    />
    <input
      type="number"
      min="0"
      max="100"
      v-model="formData.parformance1"
      placeholder="1. Performans"
    />
    <input
      type="number"
      min="0"
      max="100"
      v-model="formData.parformance2"
      placeholder="2. Performans"
    />
    <input
      type="number"
      min="0"
      max="100"
      placeholder="Ortalama"
      v-bind:value="formData.average"
      readonly
    />
    <input
      type="text"
      minlength="0"
      maxlength="5"
      placeholder="Durum"
      ref="result"
      v-bind:value="formData.status ? 'Geçti' : 'Kaldı'"
      readonly
    />
    <button>Hesapla</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      formData: {
        exam1: null,
        exam2: null,
        parformance1: null,
        parformance2: null,
        average: null,
        status: false,
      },
    };
  },
  methods: {
    calculate() {
      if (
        (this.formData.exam1 == 0 || this.formData.exam1 == null) &&
        (this.formData.exam2 == 0 || this.formData.exam2 == null) &&
        (this.formData.parformance1 == 0 ||
          this.formData.parformance1 == null) &&
        (this.formData.parformance2 == 0 || this.formData.parformance2 == null)
      ) {
        this.$refs["result"].value = "Lütfen boş alan bırakmayınız :)";
      } else {
        let total =
          Number(this.formData.exam1) +
          Number(this.formData.exam2) +
          Number(this.formData.parformance1) +
          Number(this.formData.parformance2);
        this.formData.average = Number(total) / 4;
        this.formData.average >= 50
          ? (this.formData.status = true)
          : (this.formData.status = false);
      }
    },
  },
};
</script>

<style lang="scss" scoped>
form {
  padding: 0 20px;
  width: 320px;
  display: flex;
  align-items: stretch;
  justify-content: space-evenly;
  flex-direction: column;
  background: #f8f8f8;
  border-radius: 6px;
  height: 480px;
  margin: auto;
  input {
    border: 2px solid var(--primary);
    border-radius: 4px;
    padding: 8px 12px;
    font-weight: 600;
    color: #272727;
    &[type="text"] {
      text-align: center;
    }
    &:read-only {
      background: #e8e8e8;
    }
  }
  button {
    font-weight: 700;
    color: var(--primary);
    border-radius: 4px;
    background: #f8f8f8;
    padding: 10px 0;
    cursor: pointer;
    border: 2px solid var(--primary);
    transition: all 300ms ease-in-out;
    &:hover {
      background: var(--primary);
      color: #f8f8f8;
    }
  }
}
</style>
