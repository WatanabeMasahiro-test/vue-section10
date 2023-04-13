<template>
    <div class="container">
        <!-- <p v-border:dotted="{width: '5px', color: 'red'}">Home</p> -->
        <p v-border2:solid.round.shadow="{width: '10px', color: 'blue'}">Global</p>
    </div>
</template>

<script>
export default {
  name: 'GlobalComp',
  data: () => ({
    /**
     * ローカルにカスタムディレクティブを使う場合は、「this」が使えない
     */
    tmpData : "HELLO-TEST",
}),
  directives: {
    border2(el, binding) {
        /**
         * this.tmpData = "こんにちは-テスト";
         */
        // el.style.border = "solid black 2px";
        el.style.borderWidth = binding.value.width;
        el.style.borderColor = binding.value.color;
        el.style.borderStyle = binding.arg;
        if (binding.modifiers.round) {
            el.style.borderRadius = "2.5rem";
        }
        if (binding.modifiers.shadow) {
            el.style.boxShadow = "0 2px 5px rgba(0, 0, 0, 0.26)";
        }
    }
  },
}
</script>