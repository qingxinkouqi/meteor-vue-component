<template lang="jade">
.post
  .message {{data.message}}
    a.action(@click="removePost") x
</template>

<script lang="coffee">
`import {Meteor} from 'meteor/meteor'`

return {
  props: [ 'data' ]
  methods:
    removePost: ->
      Meteor.call 'posts.remove', @data._id
  created:
    console.log 'Post'
}
</script>

<!-- Project path test -->
<style scoped lang="less">
// Import
@import "~imports/ui/mixins.less";

a {
  text-decoration: underline;
}

.post {
  margin: 6px 0;

  .message {
    // Mixin
    .padding(12px);
  }
}
</style>

<!-- Relative path test -->
<style scoped lang="less">
// Import
@import "../../imports/ui/mixins.less";

.post {
  .message {
    .border-radius(3px);
  }
}
</style>

<!-- Project path test -->
<style lang="sass">
@import ~imports/ui/colors.sass

.message
  color: $message-color
</style>

<!-- Relative path test -->
<style lang="sass">
@import ../../imports/ui/colors.sass

.message
  background-color: $message-background
</style>
