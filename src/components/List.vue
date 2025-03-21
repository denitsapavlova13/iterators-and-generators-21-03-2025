<script setup lang="ts">
import ListItem from './ListItem.vue'
import DocumentationIcon from './icons/IconDocumentation.vue'
import IconSupport from './icons/IconSupport.vue';

const iteratable = [1, 2, 3, 4, 5];

function showDemoArray() {
  console.log(iteratable);
}

</script>

<template>
  <ListItem>
    <template #icon>
      <DocumentationIcon />
    </template>
    <template #heading>Iteratable</template>
      Iterable objects are objects that implement the Iterable interface.
      That is, iterable objects expose a default iteration method, allowing them to define or customize their iteration behavior.
      <button @click="showDemoArray"> Example </button>

      <ul>
        <li> Any object that contains a <code>[Symbol.iterator]</code> method is an iterable object. </li>
        <li> Several built-ins such as <i>Array</i>, <i>Set</i>,<i> String</i> and
        <i> Map </i> define a default iteration behavior, while others such as <i>Object</i> do not.</li>
      </ul>
  </ListItem>
  <ListItem>
    <template #icon>
      <DocumentationIcon />
    </template>
    <template #heading> Iterator </template>
      Iterator objects are objects that implement the Iterator interface.
      That is, iterator objects must have a next method that returns a result object in the <code>{ value: Any, done: Boolean }</code> format.

    <pre>
        <code class="custom-code">
          const iterable = ['1', '2', '3'];

          const iterator = iterable[Symbol.iterator]();
          iterator.next(); // { value: '1', done: false }
          iterator.next(); // { value: '2', done: false }
          iterator.next(); // { value: '3', done: false }
          iterator.next(); // { value: undefined, done: true }
        </code>
    </pre>
  </ListItem>
  <ListItem>
    <template #icon>
      <DocumentationIcon />
    </template>
    <template #heading> Generator </template>
      Generator functions are a special kind of function that return a <i>Generator object</i>.
      This object conforms to both the <i>iterable protocol</i> and the <i>iterator protocol</i>.

      <pre>
        <code class="custom-code">
          function* generator(i) {
            yield i;
            yield i + 10;
            yield i + 20;
          }

          const gen = generator(10);

          console.log(gen.next().value); // 10
          console.log(gen.next().value); // 20
          console.log(gen.next().value); // 30
          console.log(gen.next().value); // undefined
        </code>
      </pre>
  </ListItem>
  <ListItem>
    <template #icon>
      <IconSupport />
    </template>
    <template #heading> Where can I use this? </template>
      <ul>
        <li> Use a generator with <code>yield</code> for async handling. </li>
        <pre>
          <code class="custom-code">
            async function* asyncHandler () {
              console.log('Step 1: Start');
              yield new Promise((resolve) => setTimeout(() => resolve('Step 2: Fetch Data'), 1000));
              yield new Promise((resolve) => setTimeout(() => resolve('Step 3: Fetch Data 2'), 1000));
              yield new Promise((resolve) => setTimeout(() => resolve('Step 4: Done!'), 1000));
            }
          </code>
        </pre>
        <li> Infinite scrolls and paginated API requests <i>(lazy loading)</i> </li>
        <pre>
          <code class="custom-code">
          async function* fetchNewPage() {
            let page = 0;
            while (true) {
              const response = await fetch(`fancy-api-call-here-for-paginated data`);
              if (response.length === 0) return;
              yield* response;
              page++;
            }
          }
          </code>
        </pre>
        <li> Counter generator </li>
        <pre>
          <code class="custom-code">
            function* counter() {
              let i = 0;
              while (true) {
                yield i++;
              }
            }
          </code>
        </pre>
     </ul>
  </ListItem>
</template>

<style lang="css" scoped>
code{
  padding: 2px 4px;
  font-size: 90%;
  color: steelblue;
  background-color: #f8f8f2;
  border-radius: 4px;
}

i {
  color: steelblue;
}

.custom-code {
  font-family: "Fira Code", monospace;
  padding: 10px;
  border-radius: 5px;
  display: block;
  overflow-x: auto;

  color: steelblue;
  background-color: #f8f8f2;
}

button{
  border-radius: 6px;
  border: none;
  color: white;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  cursor: pointer;
  padding: 2.5px;

  background-color: steelblue;
}
</style>
