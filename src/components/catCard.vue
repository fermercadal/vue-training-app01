<template>
  <li>
    <h2>{{ name }} <span v-if="isFavorite">(Favorite)</span></h2>
    <button @click="toggleDetails">Show details</button>
    <button @click="toggleFavorite">Toggle favorite</button>
    <ul v-if="detailsAreVisible">
      <li>Color: {{ color }}</li>
      <li>AKA: {{ codeName }}</li>
    </ul>
  </li>
</template>

<script>
export default {
  name: 'catCard',
  props: {
    id: {
      typpe: String,
      required: true,
      validator: value => {
        return value !== '' && value !== ' ';
      }
    },
    name: {
      typpe: String,
      required: true
    },
    color: {
      typpe: String,
      required: true
    },
    codeName: {
      typpe: String,
      required: false,
      default: 'gato'
    },
    isFavorite: {
      typpe: Boolean,
      required: false,
      default: true
    }
  },
  data() {
    return {
      detailsAreVisible: false
    }
  },
  methods: {
    toggleDetails() {
      this.detailsAreVisible = !this.detailsAreVisible;
    },
    toggleFavorite() {
      this.$emit('toggle-favorite', this.id);
    }

  }
}
</script>