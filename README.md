# checking both v-model and v-bind:value used on same element is conflicted with customizing component v-model

### Version

2.5.5

### Reproduction link

[https://github.com/VdustR/vue-model-issue-reproduction](https://github.com/VdustR/vue-model-issue-reproduction)

### Steps to reproduce

```text
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev
```

### What is expected?

Compiled successfully.

### What is actually happening?

Got error:

```text
 - :value conflicts with v-model on the same element because the latter already expands to a value binding internally
```

---
The new improvements from v2.5.5

> warn if both v-model and v-bind:value are used on same element

is conflicted with [Customizing Component `v-model`](https://vuejs.org/v2/guide/components.html#Customizing-Component-v-model).

Downgrade the vue(vue-template-compiler exactly) in the reproduction to 2.5.4 and it will be compiled successfully.

BTW,
Production vue.js works fine -> [CodePen](https://codepen.io/VdustR/pen/vWpOvv)

[vue#7084](https://github.com/vuejs/vue/issues/7084)
[vue-material#1167](https://github.com/vuematerial/vue-material/issues/1167)
