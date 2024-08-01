<script setup>
</script>

<template>
  <div>
    <form>
      <div>
        <h3>Timer</h3>
        <p>{{ count }}</p>
      </div>
      <div>
        <input v-model.trim="name" @change="sum">
      </div>
      <div>
        <input v-model.lazy="lastName" @change="sum">
      </div>
      <div>
        <h1>Result will come here</h1>
        <div style="display: flex">
          <p>{{ result }} </p>
          <p v-if="agree">(Agreed)</p>
        </div>
      </div>
      <input type="checkbox" v-model="agree" style="margin-top: 10px"> Agree?

      <h3 style="margin-top: 10px">Elements</h3>
      <div v-for="(a, index) in array" style="display: flex; align-items: center; gap: 10px">
        <p>{{ a }}</p>
        <a @click="removeElement(index)">Remove</a>
      </div>
      <br>
      <button v-if="agree">Submit</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      appName: 'Initial Vue App',
      count: 0,
      lastName: '',
      agree: false,
      array: ['A', 'B', 'C'],
      name: '',
      result: 0,
      i: 0
    };
  },
  methods: {
    increment() {
      this.count++;
    },
    sum() {
      this.result = this.name + " " + this.lastName;
    },
    removeElement(index) {
      this.array.splice(index, 1);
    }
  },
  created() {
    setInterval(() => {
      this.count++;
    }, 1000)
  },
  watch:{
    name:function (newName,oldName){
      console.log('Name Changed From ' + oldName + ' to ' + newName)
    }
  }
}
</script>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
