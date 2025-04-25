---
theme: default
themeConfig:
  primary: '#fff'
background: /delorian_fire.png
# some information about your slides, markdown enabled
title: Vueconf 2024
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
# apply any unocss classes to the current slide
class: text-center
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# https://sli.dev/guide/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations#slide-transitions
transition: slide-left
# enable MDC Syntax: https://sli.dev/guide/syntax#mdc-syntax
mdc: true
---

<div class="font-size-10">Migrating From Vue 2 Class Components</div>
<div>Robby Helms · Web Lead @ Pocket Prep</div>

---
layout: two-cols
---

# The road ahead

<img class="max-w-400px pt-12px" src="/roads_2.jpeg">

::right::

<ul class="mt-54px">
  <li v-click="1">Pocket Prep's story
    <li v-click="2">Searching for the best Vue + TypeScript experience</li>
  </li>
  <li v-click="3">Options API <> Class Components</li>
  <li v-click="4">Class Components <> Composition API</li>
</ul>

<div v-click="1" class="flex flex-col items-center">
  <img class="max-w-120px mt-60px" src="/pocketprep.png">
  <div class="mt-12px">Pocket Prep</div>
</div>

---

# Back to ~~1955~~ 2019

<img class="absolute top-20px right-50px max-w-300px" src="/destination_time.webp">

<div class="absolute top-180px max-w-180" v-click>
  <h2>Creating a Vue 2 app with <code>@vue/cli</code></h2>
  <br>
  <img src="/vue-cli-prompt.png">
</div>

---
layout: two-cols
---

# Vue 2: Options API <> Class Components
<img class="absolute top-20px right-20px max-w-200px" src="/what.jpeg">

<div class="mt-80px" />
````md magic-move

```vue
// Vue 2 Options API
```

```vue
// Vue 2 Options API
<script>
export default {
  data () {
    return {
      someData: 'some data'
    }
  }
}
</script>
```

```vue
// Vue 2 Options API
<script>
export default {
  methods: {
    someMethod () {
      alert('a method')
    }
  }
}
</script>
```

```vue
// Vue 2 Options API
<script>
export default {
  props: {
    someProp: {
      type: String,
      default: 'some prop',
    },
  },
}
</script>
```

```vue
// Vue 2 Options API
<script>
export default {
  methods: {
    emitSomething () {
      this.$emit('something')
    }
  },
}
</script>
```

````

::right::

<div class="mt-160px" />

````md magic-move {at:1}

```vue
// Vue 2 Class Components
```

```vue
// Vue 2 Class Components
<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'

@Component
export default class Example extends Vue {
  someData = 'some data'
}
</script>
```

```vue
// Vue 2 Class Components
<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'

@Component
export default class Example extends Vue {
  someMethod () {
    alert('a method')
  }
}
</script>
```

```vue
// Vue 2 Class Components
<script lang="ts">
import { Component, Vue, Prop } from 'vue-property-decorator'

@Component
export default class Example extends Vue {
  @Prop({ default: 'some prop' }) someProp!: string
}
</script>
```

```vue
// Vue 2 Class Components
<script lang="ts">
import { Component, Vue, Emit } from 'vue-property-decorator'

@Component
export default class Example extends Vue {
  @Emit('something')
  emitSomething () {
    return true
  }
}
</script>
```

````
---

# Rockin' with Vue 2 Class Components

<div class="flex relative">
  <h3 v-click="[1, 2]" class="absolute">Waiting for Vue 3</h3>
  <h3 v-click="2" class="absolute">
    <span class="decoration-line-through pr-12px">Waiting for Vue 3</span>
    No class component support in Vue 3
  </h3>
</div>
<img v-click.hide="2" class="absolute top-140px max-w-460px max-h-380px" src="/amplifier.webp">
<img v-click="[2, 3]" class="absolute top-140px max-w-460px max-h-380px" src="/loud-music-speakers.gif">
<img v-click="3" class="absolute top-140px max-w-460px max-h-380px" src="/blasted.jpeg">
<div v-click="4" class="absolute top-160px right-100px">
  <h5><i>...heated debates abound...</i></h5>
  <div class="mt-12px">
    Medium article with more history:
    <div>
      <a href="https://medium.com/@robert.helms1/vue-2-to-vue-3-with-class-components-cdd6530a2b2a">
        Vue 2 to Vue 3 with Class Components
      </a>
    </div>
  </div>
</div>
<div v-click="5" class="absolute top-400px right-285px">So...now what?</div>

---

# vue-facing-decorator

<img class="absolute top-20px right-20px max-w-200px" src="/flux_capacitor.gif">
<h3 v-click class="mt-12px">Migration steps</h3>
<ul>
  <li v-click><code>npm i vue-facing-decorator</code></li>
  <li v-click>Find and replace <code>'vue-property-decorator'</code> with <code>'vue-facing-decorator'</code></li>
  <li v-click>Move class properties initialized using <code>this</code> to <code>mounted</code></li>
  <li v-click><code>$emit</code> calls to <code>@Emit</code> methods</li>
  <li v-click><code>@Component({ beforeRouteUpdate() })</code> to <code>@Component({ options: { beforeRouteUpdate() } })</code></li>
  <li v-click>Optionally wrap default exports with <code>toNative()</code></li>
  <li v-click>(And all the other normal Vue 3 migration steps...)</li>
</ul>

<h3 v-click class="mt-24px">Other notes</h3>
<ul>
  <li v-click>Supports legacy experimental TS decorators and stage 3 proposal decorators (via <code>toNative</code>)</li>
  <li v-click>Upcoming beta release to ship CommonJS and ES module versions of the package</li>
</ul>

---
layout: center
---

<div class="flex flex-col items-center">
  <h1 v-click>Back</h1>
  <h1 v-click>to</h1>
  <h1 v-click>the</h1>
  <h1 v-click>Composition API</h1>
</div>


---
layout: two-cols
---

# Vue 3: Composition API <> Class Components

<img class="absolute top-20px right-58px max-w-240px" src="/hoverboard.png">
<div class="mt-80px" />

````md magic-move {at:1}

```vue
// Vue 3 Class Components
```

```vue
// Vue 3 Class Components
<script lang="ts">
import { Component, Vue } from 'vue-facing-decorator'

@Component
export default class Example extends Vue {
  someData = 'some data'
}
</script>
```

```vue
// Vue 3 Class Components
<script lang="ts">
import { Component, Vue } from 'vue-facing-decorator'

@Component
export default class Example extends Vue {
  someMethod () {
    alert('a method')
  }
}
</script>
```

```vue
// Vue 3 Class Components
<script lang="ts">
import { Component, Vue, Prop } from 'vue-facing-decorator'

@Component
export default class Example extends Vue {
  @Prop({ default: 'some prop' }) someProp!: string
}
</script>
```

```vue
// Vue 3 Class Components
<script lang="ts">
import { Component, Vue, Emit } from 'vue-facing-decorator'

@Component
export default class Example extends Vue {
  @Emit('something')
  emitSomething () {
    return true
  }
}
</script>
```

````

::right::

<div class="mt-160px" />
````md magic-move

```vue
// Vue 3 Composition API + script setup
```

```vue
// Vue 3 Composition API + script setup
<script setup lang="ts">
import { ref } from 'vue'
const someData = ref('some data')
</script>
```

```vue
// Vue 3 Composition API + script setup
<script setup lang="ts">
const someMethod = () => {
  alert('a method')
}
</script>
```

```vue
// Vue 3 Composition API + script setup
<script setup lang="ts">
defineProps<{
  someProp: string
}>()
</script>
```

```vue
// Vue 3 Composition API + script setup
<script setup lang="ts">
const emit = defineEmits<{
  something: []
}>()
</script>
```
````

---

<h1>Recap</h1>
<ul>
  <li v-click class="font-size-6">If you're using class components, let me know!</li>
  <li v-click class="font-size-6">vue-facing-decorator can help get more apps to Vue 3</li>
  <li v-click class="font-size-6">The future for Vue + TypeScript is bright</li>
</ul>
<img v-after class="max-w-400px ml-32px" src="/family_ending.jpeg">

---
layout: center
---

<img class="max-w-400px mb-12px" src="/goodbye.png">
<div class="flex flex-col items-center">
  <h1>Thank you!</h1>
  <h6>robby@pocketprep.com</h6>
  <h6>X/formerly twitter: @helms_rob</h6>
</div>
