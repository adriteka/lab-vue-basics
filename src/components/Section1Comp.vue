<template>
  <section class="section has-text-centered">
    <div class="operation">
      <p class>El resultado de</p>
      <input type="number" v-model="num1" class="num input" />
      <p>+</p>
      <input type="number" v-model="num2" class="num input" />
      <p>es igual a {{ num1 + num2 }}</p>
    </div>
    <div class="operation">
      <p class>El resultado de</p>
      <input type="number" v-model="num3" class="num input" />
      <p>+</p>
      <input type="number" v-model="num4" class="num input" />
      <p>es igual a {{ sum(num3, num4) }}</p>
    </div>
    <div class="box caja-de-circulo" :style="bgColor">
      <div v-show="isChecked" class="circulo"></div>
    </div>
    <div class="box-ops">
      <input type="checkbox" id="checkbox" v-model="isChecked" />
      <label for="checkbox">Muestra el círculo</label>
      <button @click="nextColor()" class="button">Cambia fondo</button>
    </div>
    <div class="columns is-multiline">
      <div
        v-for="p in posts"
        class="column is-12-mobile is-6-tablet is-4-desktop"
        :key="p.title"
      >
        <PostComp
          :title="p.title"
          :description="p.description"
          :content="p.content"
        />
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from "vue";
import PostComp from "./PostComp.vue";
const isChecked = ref(false);
const num1 = ref(1);
const num2 = ref(1);
const num3 = ref(1);
const num4 = ref(1);
const sum = (val1, val2) => {
  return val1 + val2;
};
const colors = ["white", "red", "yellow", "purple", "black"];
let indexCurrentColor = 0;

const bgColor = ref({
  backgroundColor: colors[indexCurrentColor],
});
const nextColor = () => {
    indexCurrentColor = (indexCurrentColor + 1) % colors.length;
    bgColor.value.backgroundColor = colors[indexCurrentColor];
};

const posts = [
  {
    title: "Lorem ipsum dolor sit amet consectetur adipisicing",
    description:
      "Lorem ipsum dolor sit amet consectetur, adipisicing elit. Totam quidem culpa nulla delectus distinctio! Eum quod asperiores fuga saepe obcaecati!",
    content:
      "Lorem ipsum dolor sit amet consectetur adipisicing elit. Dolorum iure placeat cupiditate pariatur voluptas vel sapiente atque harum minus repellat inventore possimus nobis quidem cum, autem aut, suscipit fuga similique cumque quibusdam accusantium ipsum eveniet in. Mollitia ut dolore nemo! Porro nihil ea laborum vero voluptates amet dolorum error in neque eligendi cupiditate, tempore enim nulla. Beatae tempora repudiandae dolores eum nisi minima quibusdam soluta, delectus commodi natus nobis rerum.",
  },
  {
    title: "Quia ipsum autem voluptatum quaerat officiis numquam",
    description:
      "Repellat officiis aut deserunt corrupti dignissimos? Temporibus corrupti eum excepturi ut ad laboriosam exercitationem eius repellat tempora odio.",
    content:
      "Lorem ipsum dolor sit amet consectetur adipisicing elit. Sequi doloribus vitae placeat, nihil laborum modi pariatur voluptate unde autem eos! Optio pariatur ad id quo asperiores! Culpa molestiae expedita consectetur magnam. Minima, corrupti pariatur asperiores expedita aspernatur rerum saepe nisi earum laborum quasi voluptate temporibus non assumenda a. Neque assumenda nulla reiciendis sequi nesciunt vitae, voluptate recusandae nostrum. Incidunt doloribus dolorum officia reprehenderit temporibus exercitationem modi delectus est quasi aperiam, quibusdam maxime cum maiores? Inventore vitae officiis eum repudiandae recusandae.",
  },
  {
    title: "Reiciendis dignissimos fugiat pariatur tempora?",
    description:
      "Explicabo non pariatur eum cum modi facilis inventore unde, quidem praesentium repellendus qui autem.",
    content:
      "Lorem ipsum dolor sit amet consectetur adipisicing elit. Quis autem rerum alias, dolore suscipit ipsam molestiae quod. Quam voluptas commodi laudantium laboriosam ipsam eos impedit adipisci consequatur, tempore accusamus ducimus nam fuga esse alias, nesciunt expedita odio similique a sunt odit maxime iure atque, nulla sequi! Illum quis possimus quisquam delectus esse dicta. Facere fugit, cumque enim hic doloribus dolore non, sunt eligendi laudantium expedita libero aliquam veniam doloremque? Reprehenderit porro quidem numquam expedita neque?",
  },
];
</script>

<style scoped>
.operation {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 1ch;
  margin: 1rem;
}

.operation p {
  font-size: large;
}

.num {
  width: 9ch;
}
.box-ops {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 1rem;
  margin-top: 2rem;
  margin-bottom: 4rem;
}

.box {
  height: 8rem;
  padding: 1rem;
  aspect-ratio: 1;
  margin: 2rem auto;
}

.circulo {
  height: 6rem;
  aspect-ratio: 1;
  border-radius: 50%;
  background-color: blue;
  color: #4a4a4a;
}
</style>
