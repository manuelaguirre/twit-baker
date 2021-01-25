<template>
  <tweet-area
    @keydown="handleKeyDown($event)"
    @update:modelValue="updateFullText()"
    v-for="tweet in tweets"
    :key="tweets.indexOf(tweet)"
    v-model="tweet.text"
  />
  <strong>{{ fullText }}</strong>
</template>

<script>
import { ref } from 'vue';

import TweetArea from "./TweetArea.vue";

export default {
  components: {
    TweetArea,
  },

  data() {
    return {
      fullText: "",
      tweets: [{ text: "Write thread here." }],
    };
  },

  methods: {
    createEmptyTweet() {
      this.tweets.push({
        text: "",
      });
    },

    updateFullText() {
      const tweetTexts = this.tweets.map((tweet) => {
        return tweet.text;
      });
      this.fullText = tweetTexts.join("\n");
    },

    handleKeyDown(event) {
     
        if (event.shiftKey && event.key === "Enter") {
          if (!this.isLastTweetEmpty) {
            this.createEmptyTweet();
          }
          event.preventDefault();
          
        }
    },
  },

  computed: {
    isLastTweetEmpty() {
      return this.tweets[this.tweets.length - 1].text === "";
    },
  },
};
</script>

<style></style>
