<template>
  <div>
    <ul class="tag-group">
      <li class="tag-item" @click="changeToAll"><div :class="allTag">All</div></li>
      <li class="tag-item" @click="changeToDone"><div :class="doneTag">Done</div></li>
      <li class="tag-item" @click="changeToWaiting"><div :class="waitingTag">Waiting</div></li>
    </ul>
  </div>
</template>
<script>
export default {
  props: ['group'],
  methods: {
    changeToAll() {
      this.$emit('groupChanged', "all");
    },
    changeToDone() {
      this.$emit('groupChanged', "done");
    },
    changeToWaiting() {
      this.$emit('groupChanged', "waiting");
    }
  },
  computed: {
    allTag() {
      return (
        this.group === "all"
        ?{active: true}
        :{active:false}
      )
    },
    doneTag() {
      return (
        this.group === "done"
        ?{active: true}
        :{active:false}
      )
    },
    waitingTag() {
      return (
        this.group === "waiting"
        ?{active: true}
        :{active:false}
      )
    }
  }
}
</script>
