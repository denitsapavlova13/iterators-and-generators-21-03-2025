<script setup lang="ts">
import List from './components/List.vue';

const iteratableArrayOfNumbers = [1, 2, 3, 4, 5];

const iteratableArrayOfStrings = ['John', 'Jane', 'Mary', 'Pete'];

const result = iteratableArrayOfStrings.filter(name => name.includes('a')).map(name => `The name of the person is ${name}`);

function reverseArrayIterator(array: number[]) {
  return{
    [Symbol.iterator](){
      let index = array.length;
      return {
        next() {
          return {
            value: array[--index],
            done: index < 0,
          }
        }
      }
    }
  }
}

function* reverseArrayGenerator(array: number[]) {
  let index = array.length;
  while(index > 0)
  {
    yield array[--index];
  }
}



function* formatNames(names: string[]){
  for(const name of names){
    if (name.includes("y")) {
      yield `The name of the person is ${name}`;
    }
  }
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
