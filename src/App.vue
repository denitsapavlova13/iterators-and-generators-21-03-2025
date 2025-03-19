<script setup lang="ts">
import List from './components/List.vue';

const iteratableArrayOfNumbers = [1, 2, 3, 4, 5];

const iteratableArrayOfStrings = ['John', 'Jane', 'Mary', 'Pete'];
const result = iteratableArrayOfStrings.filter(name => name.includes('a')).map(name => `The name of the person is ${name}`);


function reverseArrayIterator (array: number[]){
  // TO DO: Implement the reverseArrayIterator function
  // Hint: Use the Symbol.iterator property
}

function* reverseArrayGenerator(array: number[]) {
  // TO DO: Implement the reverseArrayGenerator function
  // Hint: Use the yield keyword
}

function* formatNames(names: string[]){
  // TO DO: Implement the formatNames generator function
}

</script>

<template>
  <header>
  <h2> Frontend Guild meeting 21-03-2024 </h2>
  </header>

  <main>
    <List />
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;

h2 {
    color: steelblue;
    font-weight: bold;
  }
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
